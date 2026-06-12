---
title: "SDL c++ help"
date: 2012-01-18
forum: General Help
---

### Post by AlexShalex on 2012-01-18
Hi, I just finished writing my game (messy code i know, but i do OOP now) in c++, SDL and Opengl;

It is two player and shares the same keyboard for controls:
p1: w,a,s,d
p2: arrow keys (OR) l, ;, ", p

My issue is that when i hold the "down" and the "right" arrow keys simultaneously,
player 2 (w,a,s,d) cannot move right at all. I hold "d" and nothing happens, but ONLY when i hold those two keys.

Similarly, when i hold "w" and "d" , moving diagonally up, for player 2. Player one CAN move right, but not down and right(diagonally down).
Should i make two events- one for each player? Pleass help... Thankyou very much

here is just the important code that relates to my problem:

...
//when key is pressed down it is set to true.
if (event.type==SDL_KEYDOWN)

//Player 2
if (event.key.keysym.sym == SDLK_w) w = true; 
if (event.key.keysym.sym == SDLK_a) a = true;
if (event.key.keysym.sym == SDLK_s) s = true;
if (event.key.keysym.sym == SDLK_d) d = true;

//Player 1
if (event.key.keysym.sym == SDLK_RIGHT) right = true;
if (event.key.keysym.sym == SDLK_LEFT)  left = true;
if (event.key.keysym.sym == SDLK_UP)    up = true;
if (event.key.keysym.sym == SDLK_DOWN)  down = true;

}
//and the same thing again but if the key is released- it's set to false

        if (w == true  ) y2-=0.44;
        if (s == true  ) y2+=0.44;
        if (a == true  ) x2-=0.44;
        if (d == true  ) x2+=0.44;

        if (right == true)  myX +=0.44;
        if (left == true )  myX -=0.44;
        if (down == true )  myY +=0.44;
        if (up == true   )  myY-= 0.44;

---

