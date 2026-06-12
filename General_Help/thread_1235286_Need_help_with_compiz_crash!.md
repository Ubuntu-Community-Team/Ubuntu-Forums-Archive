---
title: "Need help with compiz crash!"
date: 2009-08-08
forum: General Help
---

### Post by xxarthur33xx on 2009-08-08
I was messing around and ended the compiz.real process, so i went to restart and login, and I get a screwed up screen and I cant login. How do I fix this?

---

### Post by xxarthur33xx on 2009-08-08
Anyone?!? This is really making me mad...

---

### Post by xxarthur33xx on 2009-08-09
Ok, well I booted into safemode and did the shell + networking and did
```
sudo apt-get remove compiz
```
and then
```
sudo apt-get install compiz
```

and I tried booting back in, and it is still doing the same thing. It boots up. shows the loading bar, then when it gets to the login screen it goes all wierd colors and twitches. I try ctrl+alt+f1 and nothing happens, tried ctrl+alt+delete and nothing happens.

Anyone know what it may be?

---

### Post by coldReactive on 2009-08-09
Edit, nevermind.

---

### Post by SPARTAN-118 on 2009-08-09
What do you mean, "edit, nvm"?

I'm having a similar problem;

after enabling "Blur Windows" effect in Compiz-Config, now my screen's all messed up.

I have a Wubi install, so I can't go in to recovery mode.

How do I change the settings back to normal, if I can't even get in?

I can tell you this right now:

I am *not* re-installing Ubuntu without backing up my files.

---

### Post by xxarthur33xx on 2009-08-09
Ok, well im using my live cd to check on files and to access the internet.

I just tried uninstalling compiz-core and for some reason when i go into home, .compiz is still there.

Would it be compiz that is messing me up? Im guessing it is because thats the only thing that I clicked on before It screwed up.

Is there anything else that i should be uninstalling?

---

### Post by overdrank on 2009-08-09
> **SPARTAN-118 said:**
> What do you mean, "edit, nvm"?

I'm having a similar problem;


I have a Wubi install, so I can't go in to recovery mode.


I am *not* re-installing Ubuntu without backing up my files.
Hi and I believe you can reach recovery mode with wubi, you can use the escape key when ubuntu is highlighted at the grub.
> **xxarthur33xx said:**
> Ok, well im using my live cd to check on files and to access the internet.

I just tried uninstalling compiz-core and for some reason when i go into home, .compiz is still there.

Would it be compiz that is messing me up? Im guessing it is because thats the only thing that I clicked on before It screwed up.

Is there anything else that i should be uninstalling?
Hi and have you tried using the xfix option when booting into recovery mode? :)

---

### Post by SPARTAN-118 on 2009-08-09
> **overdrank said:**
> Hi and I believe you can reach recovery mode with wubi, you can use the escape key when ubuntu is highlighted at the grub.

Hi and have you tried using the xfix option when booting into recovery mode? :)

There is no "GRUB" with Wubi, it's Windows Bootloader.

I read in Ubuntu Help/Support that you can press "Esc" after selecting Ubuntu, but, again, I can't edit the GRUB settings to give me more time than 3 sec. after selecting Ubuntu in Bootloader.

Well, I'll try.
I *really* hope - and pray - that I can get this fixed, and finally fully install Ubunut to another partition.

SPARTAN-118

---

### Post by abhilashm86 on 2009-08-09
well next time, you [use this compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"), this will tell you what is error,
why compiz is not working, maybe you are using more than one window managers or graphics card support or not enabled and many more, just install it,
then run in terminal ```

abhilash@abhilash:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7050/nForce 610i (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

abhilash@abhilash:~$ 

```
so its very helpful:)

---

### Post by abhilashm86 on 2009-08-09
while you un-install something, always use,
```

sudo apt-get remove purge-- <package name>

```
so it'll delete all files including hidden files  from your home directory,
then re-install the package, so no trouble while installing:)

---

### Post by SPARTAN-118 on 2009-08-09
> **abhilashm86 said:**
> well next time, you [use this compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"), this will tell you what is error,
why compiz is not working, maybe you are using more than one window managers or graphics card support or not enabled and many more, just install it,
then run in terminal ```

abhilash@abhilash:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7050/nForce 610i (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

abhilash@abhilash:~$ 

```so its very helpful:)

*grumbling about Wubi*

Love your sig, I agree, 'cept where I live we (unfortunately) *do* have Windows and Gates.

---

### Post by abhilashm86 on 2009-08-09
> **SPARTAN-118 said:**
> *grumbling about Wubi*

Love your sig, I agree, 'cept where I live we (unfortunately) *do* have Windows and Gates.

ha ha thanks:) yea its cool!!

---

### Post by xxarthur33xx on 2009-08-09
just tried that xfix or w/e it was, it didnt help. About to try that ./compiz-check now.

---

### Post by xxarthur33xx on 2009-08-09
ok, I have a problem. Since I cant login, I need to use recovery mode which is all text. I try to run the ./compiz-check, but it says that I cant do it while being root. How would I run it as non-root?

---

### Post by abhilashm86 on 2009-08-09
> **xxarthur33xx said:**
> ok, I have a problem. Since I cant login, I need to use recovery mode which is all text. I try to run the ./compiz-check, but it says that I cant do it while being root. How would I run it as non-root?

did you use sudo followed by ./compiz check?? if you are a superuser press CTRL-d to be as a normal user, i guess default user in live cd is root.

---

### Post by SPARTAN-118 on 2009-08-09
> **abhilashm86 said:**
> did you use sudo followed by ./compiz check?? if you are a superuser press CTRL-d to be as a normal user, i guess default user in live cd is root.

Wow, I'm an idiot.

I didn't try overdrank's method before posting.
How humiliating.

Anyway, you can get into recovery mode in WUBI; just select it in Windows Bootloader, then quickly press Esc to get into GRUB.

So, I will try this check, also.
Maybe you can help both of us!

EDIT: Nvm, I typed "metacity --replace" after pressing Alt+F2, now everything works. I fixed what was wrong with Compiz-config, and then switched back to "compiz --replace".
However, xxarthur33xx, you said you can't even log in (not even running blind?), so I doubt this will be of much help to you.

SPARTAN-118

---

### Post by xxarthur33xx on 2009-08-09
Tried ctrl+d and all it did was exit me out of the shell...

I'm going to try the metacity --replace and hopefully that works..

---

