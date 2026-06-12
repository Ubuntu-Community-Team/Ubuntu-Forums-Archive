---
title: "Code::Blocks C++ Error"
date: 2010-09-25
forum: General Help
---

### Post by io5cml4z on 2010-09-25
Hi, I am trying to get the example game SpaceFight from [http://www.cppgameprogramming.com/](http://www.cppgameprogramming.com/) to work, and I got an error about itoa();
I did a bit of googling and found out it didn't work on linux. Now I'm trying to replace it with something else, but I'm getting another error message. I am a complete noob to Code::Blocks, G++, and C++.
Here's the error:
> /home/[nameblocked]/C++ Projects/SpaceFight/main.cpp|46|error: invalid operands of types &#8216;char [2]&#8217; and &#8216;int&#8217; to binary &#8216;operator>>&#8217;|Here's the code:
> void updateLives(){

    char tempStr[2];
    tempStr >> myShip.GetLives();
    textout_ex( buffer, font, tempStr, 70, 460, makecol( 255, 0, 0), makecol( 0, 0, 0));

}I really want this game to work so I can see what it does, learn from it, and maybe start making games of my own.

Edit: Marking as solved. I figured it out on my own. :)

---

### Post by io5cml4z on 2010-09-25
Bump... this is a simple error!!! I can't figure it out can someone please help???

---

### Post by io5cml4z on 2010-09-25
I just noticed that there's a programming section so I reposted this in there but I'm keeping this thread because there's way more people looking at this section. But seriously, can ANYONE help me? It's just a simple build error, probably easily fixable by people more experienced than me. Please help!!! :(

---

### Post by io5cml4z on 2010-09-25
Last bump... I'm starting to lose hope. :(
 Can NO ONE fix this? :confused:

---

