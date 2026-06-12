---
title: "Macbuntu-10.04 destroyed lucid :(  help please"
date: 2010-09-02
forum: General Help
---

### Post by ninhalo5 on 2010-09-02
Well I guess I screwed up by trusting a theme today. I can now no longer access my desktop. the only way I can access ubuntu is through the recovery kernel, and logging in through the command prompt. I installed this theme using install.sh also with the package is uninstall.sh  though I can't access it through commands.

What happened is I downloaded the package,extracted it and ran the install.sh.  It went through all of the setting up that it was supposed to do and in the end looked like it was working like it was supposed to. However my compiz got shut off so I decided to turn it back on through the desktop settings. Everything looked fine, I hit ok to accept the settings then that's when my screen went haywire. Everything on the screen was blown apart so I had to reboot, hoping that would fix it. now when I try to log back in It will go to the splash screen then go all black before the login page.
 I've tried resetting Gnome with rm -rf .gnome .gnome2 .gconf .gconfd .metacity though that will not work either. I guess I need to have access to the desktop for that to work. 
I don't know what to do, can my Os be saved or am I looking at a reinstall. 
I think if I can disable compiz perhaps long enough to boot I might be able to get rid of that theme. thoug I can't find any info on how to do it. everyanswer I find is based on having the desktop running and using gtk programs such as metacity --replace.

anyone have any ideas on how I can access my desktop again?

Thank you

---

### Post by llawwehttam on 2010-09-02
Post on my blog for resetting compiz: [http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html](http://matt-linux-log.blogspot.com/2010/08/reset-bad-compizconfig-settings-in.html)

you can run metacity --replace from a command line. (press ctrl+Alt+F1 at login screen to obtain one)

---

### Post by ninhalo5 on 2010-09-02
Thank you for the reply. I'm still having issues. I checked out the blog and followed step by step but received an error

gconf -WARNING **: None of the resolved address are writable; saving configuration settings will not be possible.
Holding the shift key seems to do nothing in 10.04, I can pick the safe kernel from the grub then choose root from there, which will automatically add my name to the prompts, no signing in, so possibly this isn't the way for me to actually get to root.

I've also tried metacity --replace and received a different error, which I didn't catch. It seems that I'm only accessing the file system in read only mode.

I'm able to boot off of the live cd which I'm using at the moment, is it possible to access my normal root and do modifications this way?

At least I can copy my files over to my windows partition in case I need to restore the o/s Which I really hope don't come down to that.

I'm able to see the un-install file I need through nautilus though permissions will not allow me to run the .sh file

Possibly I can at least edit the compiz from here and try to log in, one thing I'm starting to learn about Linux is nothing is impossible if you have the knowledge :)

Thank you

---

