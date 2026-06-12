---
title: "Offline Package and Upgrade Installation- Ubuntu 10.04"
date: 2010-06-29
forum: General Help
---

### Post by ThirdEye4103 on 2010-06-29
Hello everyone at Ubuntu Forum. I am new to the Linux/Ubuntu Operating system and i was wondering if anyone here can teach me or point me in the right direction of a guide or tutorial of a way to download packages (debs, tar, etc.) from my Vista laptop (with Wi-Fi) to a USB Flash Drive or CD, preferably the first, then transfer to my desktop running nothing but Ubuntu 10.04 with absolutely no internet connection but my iPhone 3G to tether from, but ive used up about all my data and my bill doesn't change until the 13th of July. So this is the only way i have to download and upgrade my packages. 

Ive seen the way to use Keryx on the USB but it says it doesnt support any version past 8. 

I also did something with the symatic package manager. i forgot what it was called. but it made some text file. it was for being able to transfer packages from another computer. but idk what to do next.

Also i saw a thread with a bunch of Deb files all together so i wouldn't have to get the all the dependencies of the deb files. but it only listed up to version 8, so are those debs unusable on 10.04?Also i saw a thread with a bunch of Deb files all together so i wouldn't have to get the all the dependencies of the deb files. but it only listed up to version 8, so are those debs unusable on 10.04?

sorry about my spelling, I know I spelled a couple things wrong..

---

### Post by EXCiD3 on 2010-06-29
What do you mean version 8? Keryx should work with any version of Ubuntu and for sure works with 10.04. Give it a shot.

---

### Post by ThirdEye4103 on 2010-06-30
oh I misread their tutorial. it said you cant open the file on any version older than 8.10 and must do it differently. thank you for your help.


Edit: Wait wait wait, never mind i am still lost on how you got it to work on 10.04? there are no dependencies for that version for me to download to get it to work..

---

### Post by nothingspecial on 2010-06-30
This is not a nice way to use linux.

But, you can find any package available [COLOR=Magenta][here]("http://packages.ubuntu.com/karmic/")[/COLOR]

Each package lists it`s dependencies. Most packages are quite small. You could go to an internet cafe and do it, if one with bandwidth is available near you.

You get all the packages and their dependencies downloaded. Copy them into your home folder, open a terminal and type
```

sudo dpkg -i *.deb
```

Like I said, a horrible way to use something that has a package manager, but possible.

There is also [COLOR=Magenta][aptoncd]("http://aptoncd.sourceforge.net/")[/COLOR] which may or may not suit your needs better.

---

### Post by ThirdEye4103 on 2010-06-30
yeah i was also thinking about trying aptoncd. i live in a horrible area, i can only get satellite or an air card for internet it kinda blows. but my Ubuntu is on my desktop so i cant take it anywhere.

but XCIDE, i got it to work, but i cant get the GUI to come up on my Windoze Vista, all that comes up when i click the keryx.exe file in the Win32 is Command Line with absolutly no text or anything. i downloaded Python and wxPython but all i did was install them, am i supposed to do something different?

---

### Post by EXCiD3 on 2010-06-30
> **ThirdEye4103 said:**
> yeah i was also thinking about trying aptoncd. i live in a horrible area, i can only get satellite or an air card for internet it kinda blows. but my Ubuntu is on my desktop so i cant take it anywhere.

but XCIDE, i got it to work, but i cant get the GUI to come up on my Windoze Vista, all that comes up when i click the keryx.exe file in the Win32 is Command Line with absolutly no text or anything. i downloaded Python and wxPython but all i did was install them, am i supposed to do something different?

We have been having a bit of trouble with Keryx.exe lately, seems pyinstaller didn't work very well for us. Since you have Python and wxPython installed, go into the source directory and run keryx.py from there. This will run it from source and should work. If you run into any errors there, let me know.

---

### Post by ThirdEye4103 on 2010-06-30
That brought up the GUI but it crashed as soon as I tried to open the project.

I tried to see what it said on the command line but it took four trys and all I saw was Win32 is not defined. But that was only about 6% of what it said.

---

### Post by ThirdEye4103 on 2010-06-30
Okay I think I found the most simplest route to ever use to download packages without Internet connection. All I did was select packages I wanted and it automatically sellected the dependencies in synaptic package manager. Then I generated shell-script, put it on my flash drive, took it to my Vista computer, opened up the directory in firefox, used linkification and downthemall add ons to download all the debs, brought the flashdrive back to my Ubuntu desktop, and went to File>add downloaded packages in synaptic package manager and it installed em. That was quick and easy.

---

