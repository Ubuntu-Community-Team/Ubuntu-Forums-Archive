---
title: "Video resolution limited on Dell Inspiron laptop...."
date: 2006-03-16
forum: General Help
---

### Post by erdejo on 2006-03-16
Hi Y'all,

I have the same problem as Intrigue has posted in one of the older therads (from early 2005 I think....), but with me it doesn't work when using the Live CD. Seeing that that thread seems to be dead (no replies in a year) I am posting this here.
I have a Dell Inspiron 1100 and it gives me only the 640x480 option in Resolution menu. :confused: It has an integrated Intel 82845 graphics chipset. It looks like it is being recognized as such (when I go into the Device manager) but I don't have any options. I have also tried the "live vga=791" setting during boot that I read about somewhere in the posts but that also doesn't do the trick. Or is the 791 setting not the right value (the example the live cd gives me has 771....).
I am using the standard "install/run" (starting the boot from cd) of the live Cd and even tried to uncheck everything but the 1024 option when asked so during boot.
It also seems that my wireless card is not recognized or not working for I have no connection. I have to be honest and let you know that I haven't fooled with that due to the limited screen area......:cry:  But if anyone has any tips on how to go about setting that up (after fixing the video thing) then please feel free to do so....:-| 
I am also new to the Ubuntu experience, although I have tried my hands on Linux back in the early to mid nineties....:rolleyes:  Which wasn't all that bad, just limited time to put into so it kinda died....
But now I am so sick and tired of the Winblows thing thatI would like to be able to switch entirely (or as much as possible for I do a lot of 2D and 3D graphics including CAD and don't know how well Linux is equipped for this...) to this amazing free software and its community!
Anyway, to make a long story not too much longer...If anybody knows why the reso is limited to 640x480 on my Dell let me know.

Thanx in advance!

Regards, Eric

---

### Post by Ivan Matveich on 2006-03-16
n/t

---

### Post by erdejo on 2006-03-16
Huh....?????

Where do I find these files? Keep in mind I am a newbie.... to this live cd thing and fairly new to Linux in general....
And what does: n/t mean?

Anyway, thanx in advance.

Eric.

---

### Post by IYY on 2006-03-16
What he means is this, tell us the contents of the following two files:

**/var/log/Xorg.0.log ** (the log)
and
**/etc/X11/xorg.conf** (the graphical server configuration)

Most likely, you'll have to edit your xorg.conf manually and add the resolutions you want. You can view these files using a graphical text editor like **gedit**, or in terminal type **less /var/log/Xorg.0.log**.

---

### Post by erdejo on 2006-03-17
Okay, so I managed to find the files you're talking about. I have them on my USB drive. Is there a way to attach them or do I need to copy and paste the entire content of these files. Wouldn't his make the post very large?
Let me know what you want me to do.
While we're on the subject: where do these files get stored and can I edit them to use them later? Or do they get reset every time I run the Ubuntu from the Live cd? And what about all my other settings? Do i loose all of those upon shut down? :confused: 

Anyway, let me know what you guys want me to do with the files. I could even email them if you needed me to.
I looked at the files in Ubuntu using a text editor. It looks like it does select the right graphics chipset and it also seems to list all the right/possible resolution settings. Then why does it only give me the option in the resolution menu to have the 640x480 setting.  :cry: 

Thanx again in advance for your help.

---

