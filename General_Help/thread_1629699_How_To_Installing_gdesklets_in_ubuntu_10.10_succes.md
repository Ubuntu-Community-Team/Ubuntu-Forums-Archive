---
title: "How To: Installing gdesklets in ubuntu 10.10 successfully."
date: 2010-11-24
forum: General Help
---

### Post by ranjith19 on 2010-11-24
I had to search for half an hour to make gdesklets work in ubuntu. This is how it is done.

1. Open Terminal

2. Install gdeskelts by typing

[FONT="Courier New"][SIZE="2"]sudo apt-get install gdesklets[/SIZE][/FONT]

3. Create a link for python2.5

[FONT="Courier New"][SIZE="2"]sudo ln -s /usr/bin/python2.5 /usr/bin/python2.6[/SIZE][/FONT]


4. Open /usr/lib/gdesklets/utils/ErrorFormatter.py as root

[SIZE="2"][FONT="Courier New"]sudo gedit /usr/lib/gdesklets/utils/ErrorFormatter.py[/FONT][/SIZE]

5. Go to the line that contains (line 116)

[SIZE="2"][FONT="Courier New"]def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/FONT][/SIZE]

and replace it by 

[FONT="Courier New"][SIZE="2"]def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = [][/SIZE][/FONT]):

6. Thats it. Start gdesklets. It should work well. You can add it to your start-up by adding an entry in [FONT="Verdana"]gnome-session-properties[/FONT]

---

### Post by pagemaker on 2010-12-05
Great walkthrough! Worked for me... :)

---

### Post by aamil4u on 2010-12-11
Hi

Thanks a lot for your post. Ir really helped me a lot!

---

### Post by wpurcell on 2010-12-11
Yes! Many thanks from me also! Worked very well.

---

### Post by tbryancooper on 2010-12-22
When I attempt to open ErrorFormatter.py it just opens up a blank document. Any suggestions?

---

### Post by tbryancooper on 2010-12-22
NEVERMIND!!!! n00b move! I didn't capitalize the E and the F.

---

### Post by ranjith19 on 2010-12-23
open it as a superuser

---

### Post by ranjith19 on 2010-12-23
oh. okay

---

### Post by Ippo343 on 2011-01-03
Great! I finally got it working!

Thanks a lot!

---

### Post by AbdRahim on 2011-01-13
Wow! I don't know how you figure this out, but many thanks.

---

### Post by shof2k on 2011-01-17
awesome. Simple, easy to do.  Nice one!!!

---

### Post by Rich62 on 2011-02-22
Works for me!  Thanks ranjith19

---

### Post by ozone702 on 2011-02-24
Thank you!  Worked like a champ.

---

### Post by spaced-cadet on 2011-02-25
Thanks for posting this.  Worked like a charm on gdesklets v0.36.1 on 10.10

---

### Post by MrFleisch on 2011-03-04
You are my hero!!! I'm also wondering how you could figure out this, many thanks for your help!!!

---

### Post by AnaMarie on 2011-03-13
Wow! This worked! This is a very user friendly tutorial! Even a complete noob like me could figure this out with no problems! ;)

---

### Post by enigmaguy on 2011-03-16
thanks...that helped me :)

---

### Post by Hayzer on 2011-04-10
Just made an account on this in order to thank you, helped a lot!

---

### Post by BLTicklemonster on 2011-07-31
> **ranjith19 said:**
> I had to search for half an hour to make gdesklets work in ubuntu. This is how it is done.

1. Open Terminal

2. Install gdeskelts by typing

[FONT="Courier New"][SIZE="2"]sudo apt-get install gdesklets[/SIZE][/FONT]

3. Create a link for python2.5

[FONT="Courier New"][SIZE="2"]sudo ln -s /usr/bin/python2.5 /usr/bin/python2.6[/SIZE][/FONT]


4. Open /usr/lib/gdesklets/utils/ErrorFormatter.py as root

[SIZE="2"][FONT="Courier New"]sudo gedit /usr/lib/gdesklets/utils/ErrorFormatter.py[/FONT][/SIZE]

5. Go to the line that contains (line 116)

[SIZE="2"][FONT="Courier New"]def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/FONT][/SIZE]

and replace it by 

[FONT="Courier New"][SIZE="2"]def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = [][/SIZE][/FONT]):

6. Thats it. Start gdesklets. It should work well. You can add it to your start-up by adding an entry in [FONT="Verdana"]gnome-session-properties[/FONT]

Did this, and I still get nothing. Run it in terminal and it appears to run.

```

bill@bill:~$ gdesklets
Starting gdesklets-daemon...
Connected to daemon in 305 milliseconds.

```

But there's nothing there. I thought maybe if I got a desklet and put it in /gdesklets/*wherever you put stuff*, but it appears that the folks making gdesklets aren't up front about where you put stuff. (but it's linux, I'm used to that.)

So I'm just kind of stuck.

---

### Post by arvindp3 on 2012-03-24
Thanks.  Helped perfectly for 10.04

Arvind

---

