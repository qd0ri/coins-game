'''
Purpose: This is a two-player mathematical game of strategy. It is played by two
people with a pile of coins (or other tokens) between them. The players take turns removing
 coins from the pile, always removing a non-zero square number of coins (1, 4, 9, 16, …).
 The player who removes the last coin wins.
 '''
def valid_moves(n):
# list for vaild moves
    squares = [i**2 for i in range(1, int(n**0.5) + 1)]
    return [move for move in squares if move <= n]

def end(n):
    #Check if the game is end
    return len(valid_moves(n)) == 0

def play():
    """Main function to play the game"""
    n = int(input("Enter the number of coins: "))


    while not end(n):
        # Player 1's turn
        move = int(input("Player 1, choose your move: "))
        while move not in valid_moves(n):
            print("Invalid move. Please choose a valid move.")
            move = int(input("Player 1, choose your move: "))
        n -= move
        print(f"\nCurrent number of coins: {n}")
        if end(n):
            print("Player 1 wins!")
            break

        # Player 2's turn
        move = int(input("Player 2, choose your move: "))
        while move not in valid_moves(n):
            print("Invalid move. Please choose a valid move.")
            move = int(input("Player 2, choose your move: "))
        n -= move
        print(f"\nCurrent number of coins: {n}")
        if end(n):
            print("Player 2 wins!")

if __name__ == "__main__":
    play()
