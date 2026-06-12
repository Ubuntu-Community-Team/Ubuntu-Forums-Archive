---
title: "Need help in BlackJack Game!!!"
date: 2011-11-27
forum: General Help
---

### Post by jana123 on 2011-11-27
Is about BLACKJACKGAME in JAVA.
 
A player is dealt an initial hand of two cards. He has the option of drawing cards to bring the total
value to 21 or less without exceeding it, so that the dealer will have a lesser hand than the player
or by exceeding 21. The dealer also receives an initial hand of two cards. However, only the first
card is visible to all. The other card is not visible until the dealer's turn. The dealer starts his turn
after every player stood (decided to take no more cards) or busted (value above 21). A player hits
when he decides to take another card from the dealer. A player busts when his hand value is
above 21. When a player is busted, his game points in use are immediately deducted regardless
whether the dealer is busted or not. When a dealer is busted, the remaining players who are not
busted will be rewarded with the game points in use. When there is a draw between the dealer
and the player, no game points will be deducted or awarded.
Develop a Java program for the Blackjack card game. Do not implement additional options such as
"double", "split" or "surrender".
 
 
Required Functionalities
 
&#61607; User registration of up to three players (A to C).
&#61607; Player's name must be at least three characters.
&#61607; Each player is to be given 100 game points at the beginning of the game.
&#61607; Dealer has unlimited amount of game points.
&#61607; Players cannot use game points of more than what they have.
&#61607; Each player or dealer has a hand of maximum five cards.
&#61607; Enforce turn-based dealing of cards to players.
&#61607; Display the value of a player's hand after a card is dealt.
&#61607; Allow players to stand or to hit.
&#61607; A player leaves the game when he has no more game points.
&#61607; The game ends when all players have depleted all their game points.
 
Coding Restrictions
 
&#61607; You must use simple (1-D) arrays in this assignment.
&#61607; You are not allowed to use 2-D arrays, ArrayList and LinkedList as your data structures.
&#61607; You are not allowed to implement any form of GUI (E.g. Swing, AWT, etc.)

---

### Post by jana123 on 2011-11-27
Sample Output
Players Registration
B L A C K J A C K
================================================================================
Enter number of players (1-3) > 3
Enter Name of Player A > Ben
Enter Name of Player B > Joy
Enter Name of Player C > Frank
B L A C K J A C K
================================================================================
Enter number of players (1-3) > 2
Enter Name of Player A > He
*** NAME TOO SHORT!
Enter Name of Player A > Bee
Enter Name of Player B > Jude
Displaying the Game
================================================================================
Player A, You have 100 points
Enter points to use > 100
Player B, You have 100 points
Enter points to use > 100
Player C, You have 100 points
Enter points to use > 80
--------------------------------------------------------------------------------
DEALER
<Heart Ace>
--------------------------------------------------------------------------------
Player A
<Club Five>
<Club Ace>
[H]it or [S]tand S
PLAYER A : Joe
Value : 16
Hand : <Club Five> <Club Ace>
--------------------------------------------------------------------------------
Player B
<Heart Two>
<Diamond Nine>
[H]it or [S]tand H
<Spade Two>
[H]it or [S]tand H
<Diamond Four>
[H]it or [S]tand H
<Diamond Ace>
[H]it or [S]tand S
PLAYER B : Ben
Value : 18
Hand : <Heart Two> <Diamond Nine> <Spade Two> <Diamond Four> <Diamond Ace>
--------------------------------------------------------------------------------
Player C
<Spade Jack>
<Diamond Jack>
[H]it or [S]tand S
PLAYER C : Tay
Value : 20
Hand : <Spade Jack> <Diamond Jack>
--------------------------------------------------------------------------------
Page 3
DEALER
Value : 21
Hand : <Heart Ace> <Spade Queen>
DEALER
Value : 21
Hand : <Heart Ace> <Spade Queen>
================================================================================
Player A. Deducted 100 points
Player B. Deducted 100 points
Player C. Deducted 80 points
================================================================================
Player C, You have 20 points
Enter points to use > 20
--------------------------------------------------------------------------------
DEALER
<Heart Four>
--------------------------------------------------------------------------------
Player C
<Spade Ten>
<Heart Six>
[H]it or [S]tand H
<Spade Six>
PLAYER C : Tay
Value : 22
Hand : <Spade Ten> <Heart Six> <Spade Six>
--------------------------------------------------------------------------------
DEALER
Value : 14
Hand : <Heart Four> <Club Ten>
[H]it or [S]tand S
DEALER
Value : 14
Hand : <Heart Four> <Club Ten>
================================================================================
Player C. Busted. Deducted 20 points
G A M E O V E R

---

### Post by CryptAck on 2011-11-27
What kind of help do you need? Any specific logic questions?

Given the last coding restriction, I'm assuming you're coding this in Java?

---

### Post by Corporation on 2011-11-27
So you're just posting your University coursework on the forum and hoping someone will do it for you? Try asking in the programming section, and then try asking specific questions.

---

### Post by jana123 on 2011-11-27
When i try to run the code, it gives me this:
 
[SIZE=2][COLOR=#ff0000]
[LEFT][SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=black]B L A C K J A C K[/COLOR][/SIZE]
[SIZE=2][COLOR=black]====================================================[/COLOR][/SIZE]
[SIZE=2][COLOR=black]Enter number of players (1-3) > 1[/COLOR][/SIZE]
[SIZE=2][COLOR=black]Enter name of Player A > [/COLOR][/SIZE][SIZE=2][SIZE=2][COLOR=black]ben[/COLOR][/SIZE][/SIZE][SIZE=2]
[/SIZE][SIZE=2][COLOR=black]-----------------------------------------------------[/COLOR][/SIZE]
[SIZE=2][COLOR=black]Player A ,You have 100 [/COLOR][/SIZE]
[SIZE=2][COLOR=black]Enter points to use >12[/COLOR][/SIZE]
[SIZE=2][COLOR=black]------------------------------------------------------[/COLOR][/SIZE][/LEFT]

[SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000]Exception in thread "main" 
[/COLOR][/SIZE][/COLOR][/SIZE][LEFT]_[SIZE=2][COLOR=#000080][SIZE=2][COLOR=#000080]java.lang.NullPointerException[/COLOR][/SIZE][/COLOR][/SIZE]_[SIZE=2][COLOR=#000080]
[LEFT][/COLOR][/SIZE][SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000]at BlackJackGame.dealCardsToDealer([/LEFT]
[/LEFT]
[/COLOR][/SIZE][/COLOR][/SIZE][LEFT]_[SIZE=2][COLOR=#000080][SIZE=2][COLOR=#000080]BlackJackGame.java:65[/COLOR][/SIZE][/COLOR][/SIZE]_[SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000])[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#ff0000]
[LEFT][SIZE=2][COLOR=#ff0000]at BlackJackGame.start([/COLOR][/SIZE][/LEFT]
[/LEFT]
[/COLOR][/SIZE][LEFT]_[SIZE=2][COLOR=#000080][SIZE=2][COLOR=#000080]BlackJackGame.java:28[/COLOR][/SIZE][/COLOR][/SIZE]_[SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000])[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#ff0000]
[SIZE=2][COLOR=#ff0000]at BlackJackGameMain.main([/COLOR][/SIZE][/COLOR][/SIZE]_[SIZE=2][COLOR=#000080][SIZE=2][COLOR=#000080]BlackJackGameMain.java:4[/COLOR][/SIZE][/COLOR][/SIZE]_[SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000])[/COLOR][/SIZE]
[/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#ff0000]
 
[LEFT][SIZE=2][COLOR=#ff0000][COLOR=black]What does it means by _[COLOR=#000080]java.lang.NullPointerException[/COLOR]_?[/COLOR][/COLOR][/SIZE][COLOR=#ff0000][/LEFT]
[/COLOR][/COLOR][/SIZE]
[/LEFT]

---

### Post by Elfy on 2011-11-27
Closed.
> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

