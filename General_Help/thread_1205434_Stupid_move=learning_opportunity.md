---
title: "Stupid move=learning opportunity"
date: 2009-07-06
forum: General Help
---

### Post by ponychaser on 2009-07-06
Go ahead and laugh, I deserve it. I am selling a laptop with Mint 6 installed, and while cleaning it out and prepping it for the handover, I decided to try a shortcut. 

so I copied my Home directory and renamed it from 'myname' to 'hisname'.

then deleted mine.

As soon as I did it I knew it was stupid-why, just think of all those .hidden files in there...

In my defense, it was very late at night, and I was in a hurry, and I'm no rocket scientist...

So then I used the 'mv' command to rename the 'hisname' folder to 'myname' again, it will boot into the login screen, but starting the Xserver, I get a black screen  with my mouse pointer movable in it, but no other elements...

It is kind of a good opportunity for me to learn some CLI stuff, I hear the best way to learn is to break your system in various ways, and put it back together...

Any suggestions?

---

### Post by kpkeerthi on 2009-07-06
Just create a new 'Guest' user and remove yours.

---

### Post by j7%&lt;RmUg on 2009-07-06
Lol, Ah well most people(including me) do something stupid before they learn what NOT to do.

I really do hope for you sake that you dont do it again.

+1 to kpkeerthi's answer.

---

### Post by ponychaser on 2009-07-06
yeah,I guess I just have to RTFM and figure out how to do that using the CLI...

---

### Post by nothingspecial on 2009-07-06
```
sudo adduser bob
```

Follow the prompts and you have a new user called bob

bob will need admin privaledges

```
sudo adduser bob admin
```

---

### Post by ponychaser on 2009-07-06
why...thank you very much!

---

### Post by tgalati4 on 2009-07-06
Tell your friend his name is now bob.

---

