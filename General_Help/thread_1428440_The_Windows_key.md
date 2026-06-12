---
title: "The Windows key"
date: 2010-03-12
forum: General Help
---

### Post by Thrasyllus on 2010-03-12
How does one redefine the useless Windows key in the bottom left area of a keyboard? I am using a standard-issue French-Canadian keymap which for some cretinous reason does not provide a backslash! I vaguely recall that the command is: 
 
keycode [some number] = backslash 
 
What is the number for the Windows key?
 
Will this work from the command line?

---

### Post by linuxman94 on 2010-03-12
Run the xev command. Press the windows key and look at the output for this:

```
KeyRelease event, serial 36, synthetic NO, window 0x5600001,
    root 0x189, subw 0x0, time 2157439, (42,-10), root:(796,525),
    state 0x50, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

There is the keycode.

```
KeyRelease event, serial 36, synthetic NO, window 0x5600001,
    root 0x189, subw 0x0, time 2157439, (42,-10), root:(796,525),
    state 0x50, [COLOR="Red"]keycode 133[/COLOR] (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Thrasyllus on 2010-03-12
Thanks linuxman94! On my system it's 115, but that's the information I need.
 
Unfortunately bash does not recognize "keycode" as a command. So I still can't turn the key into a backslash. What to do? (I used to define my own keymap with every new distribution in the days of Slackware and Fedora, but I've forgotten the syntax - getting old, I guess.)

---

### Post by Slim Odds on 2010-03-12
> **Thrasyllus said:**
> Thanks linuxman94! On my system it's 115, but that's the information I need.
 
Unfortunately bash does not recognize "keycode" as a command. So I still can't turn the key into a backslash. What to do? (I used to define my own keymap with every new distribution in the days of Slackware and Fedora, but I've forgotten the syntax - getting old, I guess.)

Note that the "Windows" key is more like the ALT key than a normal character key. It's usually used in combination with some other key.

---

### Post by Thrasyllus on 2010-03-13
Bump.
 
Thanks to responders. Now what do I have to do to give effect to the directive
 
keycode 115 = backslash 
?

---

### Post by Slim Moe on 2010-03-13
Take a look at xmodmap.

---

### Post by Thrasyllus on 2010-03-13
> **Slim Moe said:**
> Take a look at xmodmap.
Thank you, Slim Number Two! That was the information I needed. 
 
One must write a file with the desired assignments. In my case, let's say the filename is .filename and it contains

keycode 115 = backslash 

Then one can invoke on the fly: xmodmap .filename 

And it works! For some reason the man page about xmodmap gives examples with keysym names beginning with capital letters, e.g. Backslash. When I tried this, xmodmap gave me an error message (although it didn't say why); but it accepts all-lower-case names. 

Now how can I accomplish the same thing on a virtual TTY terminal? I don't like to work in the GUI all the time.

---

### Post by Slim Moe on 2010-03-13
Actually, depending on the amount of modifications you are going to need, you can use it straight from the command line.

```
xmodmap -e "keycode 133 = backslash"

```Take a closer look at [rc.local]("https://help.ubuntu.com/community/RcLocalHowto") and you should be fine.

---

### Post by Thrasyllus on 2010-03-13
Thanks once again, Slim Moe! The xmodmap command works both ways but I'll settle for a file - knowing me, I'll get carried away amending the keyboard to my taste.
 
I could not get the boot-up procedure to work. Incidentally, the instructions referenced near the bottom the Ubuntu page you link to are better than what is on that page. This is
 
[plope.com/Members/chrism/debian_rc_local_equiv]("plope.com/Members/chrism/debian_rc_local_equiv")
 
There seem to be errors in that Ubuntu Community Documentation page. I believe the command should be added to the file /etc/init.d/local and not to /etc/init.d/rc.local. Anyway it doesn't work either way; it has to happen after bootup.
 
And xmodmap won't work on the vanilla TTY terminals, which I like to use occasionally.

---

### Post by Baneblade on 2010-03-13
The "Windows" key is hardly useless. In Ubuntu its the "Super" key which functions as another modifier. Default is mostly for compiz effects but you can set it to anything you like.

---

