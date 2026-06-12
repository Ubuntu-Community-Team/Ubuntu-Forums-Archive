---
title: "Install Problem! Configuration defaults not installed correctly"
date: 2010-07-11
forum: General Help
---

### Post by Steptoenson on 2010-07-11
Hi,

I seem to be experiencing similar problems to others mentioned. I do not wish to return to windows as one person said, but need simple, basic guidelines to help solve this, so that I can re-access my laptop.
Please read the information I emailed to [EMAIL="gconf-list@gnome.org"][COLOR=#444444]gconf-list@gnome.org[/COLOR][/EMAIL] below;

[FONT=Arial][SIZE=2]Yesterday, when I went to shutdown my laptop, which is running Ubuntu 8.10, it seemed to freeze, so I forced it to turn off by holding down the power button. Later that day, when I tried to turn the laptop on, it logs on, takes me to login and password page, but then goes to a blank screen, with the following messages;[/SIZE][/FONT]

[FONT=Arial][SIZE=2]An error occured while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]An error occured while loading or saving configuration information for update-notifier. Some of your configuration settings may not work properly.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]The details for both these messages are;[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [[COLOR=#444444]http://www.gnome.org/projects/gconf/[/COLOR]]("mhtml:{5EECB62B-8D38-4A7E-A2DC-5052A4FA2CAD}mid://00000265/!x-usc:http://www.gnome.org/projects/gconf/") for information. (Details -1 : Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))[/SIZE][/FONT]

[FONT=Arial][SIZE=2]There was also a message in the bottom right corner of the same screen;[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Install problem![/SIZE][/FONT]

[FONT=Arial][SIZE=2]The Configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.[/SIZE][/FONT]


[FONT=Arial][SIZE=2]I have been to the suggested website, which is why I am sending you this email. I do not have any technical knowledge of computers, and could not figure out how to get all the information you requested, such as which version of GConf I have installed, Output of ps jaxwww / grep gconf, Output of gconf-sanity-check-1 or gconf-sanity-check-2, and what appears in user.*syslog.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I have tried to find out this information, but I do not know how to, and need very simple instructions to help me fix this problem.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I do hope you can be of assistance in this matter. I look forward to hearing from you.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Thank you in advance of your help,[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Richard :)[/SIZE][/FONT]

---

### Post by mörgæs on 2010-07-12
Please don't double-post.

Ubuntu 8.10 is not supported, and if a bug is discovered, you can not expect it to be solved. I would go for a clean install (not upgrade) of 10.04 as soon as possible.

---

### Post by Steptoenson on 2010-07-12
Hi,
 
Apologies for double posting. My first post was as a reply to a similar problem. Afterwards, I thought this might not be noticed, so decided to post my problem as a new thread, as well.
 
Thanks for the advice regards a clean install of 10.04. How can I do this as I cannot get onto the desktop on my laptop? I am communicating with you from my wife's computer. Can I download 10.04 onto my wife's computer and put onto CD or a memory stick? How much memory will I need roughly? And then, how can I get my laptop to install it? Will I lose any information on my laptop, such as word documents, pictures, emails, etc...with a clean install?
 
Simple instructions please, as my computer knowledge is back in the 1980's with my schooling!
 
Thankyou again, in advance of any help with this matter.
 
Regards,
 
Richard :)

---

### Post by mörgæs on 2010-07-12
You are welcome. The process is:

Download the ISO file, from which you can build the Ubuntu live CD (or USB):
[http://www.releases.ubuntu.com/lucid/](http://www.releases.ubuntu.com/lucid/)

It is 700 MB.

Boot the sick computer with this CD. Nothing will be changed on the hard drive; Ubuntu is only running in memory. You have read access to all the old files, and now you can copy them to a USB memory stick.

Be patient, running Ubuntu from a CD is a slow process. 

When you have copied all files onto the USB stick, you remove it for safety. You will see an icon on the desktop saying 'install Ubuntu to disk' - here you go. 

Somewhere in the process Ubuntu will ask whether it should install 10.04 next to the old Ubuntu or use the entire disk. Choose the latter.

That's about it. Remember to have wired internet access during the process.


Have fun with 10.04!

---

### Post by Steptoenson on 2010-07-14
Hi,
 
Thank you again for replying to me, and for your advice.
 
I have downloaded ubuntu-10.04-netbook-i386 I think this is the right one. My laptop is an HP compaq nx9110 running on an intel pentium processor. Is this the right ISO file or should it have been the desktop one?
 
I burned this to CD and tried to boot my laptop with it. But my CD drive is very temperamental; it doesn't work most of the time. However, it seemed to be accessing the CD, but after the login page with username and password, the black screen appeared, with the same error messages.
 
I do not know whether I did something wrong or if the CD drive was not working properly.
 
Should I be going into the setup menu by pressing F10 to alter the boot sequence? If so, there is a problem. I do not know the setup password. The laptop is from my uncle, and he did not know the password either. Can this be bypassed, if I need to go into the setup, to tell the computer to boot using the CD?
 
Or can I put the ISO onto a USB stick? If so, do I need to remove everything else off the stick first? And how would I get my laptop to boot from the USB sick?
 
Apologies for all the questions, but as I said in my original posting, my computer days are back in the 1980's, with my schooling.
 
I hope you can continue to be of assistance with this problem.
 
Thank you,
 
Richard :)

---

### Post by mörgæs on 2010-07-14
Yes, you can boot from a USB memory stick, provided that your BIOS allows it. 

There is one guide here
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and a host of others on the web.

I would only do it on an empty USB stick. 

Maybe it is best to try a 9.10 desktop (not netbook) version for comparison. 

Last, but not least: Always remember to have wired internet access while installing.

---

### Post by mörgæs on 2010-07-14
- and on [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) you can see people's experience with getting various machines to run Ubuntu. 

Your machine is not listed, but some of his relatives are.

---

### Post by Steptoenson on 2010-07-18
Hi,
 
I think I am making some progress thanks to your help and advice.
 
The CD drive in my laptop was definitely being accessed, so I downloaded 9.10 desktop and burned to disc. My laptop booted up from the CD and I was able to find my information on the hard drive and copy to a USB stick. But some files seem locked. There is a 'X' beside their icons and I cannot copy them. The 'downloads' folder is one, but more importantly my photos folder within pictures, which has all my family photos and work related photos in. It says I do not have 'permission' and cannot change the permission, because I am not the 'owner'?
 
Also, I cannot access any of my emails, inbox and sent box. There is no evolution email. It seems I have to reactivate it, but I cannot restore old data, because I cannot find anything on the hard drive relating to my emails.
 
Can you advise or help with this please? I do not want to do a clean install until I have copied all of my files.
 
Thank you,
 
Richard :)

---

### Post by Steptoenson on 2010-07-21
Hi,
 
Sorry to trouble you again, but in addition to my last posting; discussing problems with folders that I cannot access (all photos and downloads) due to 'not having permission'; and not being able to find my old emails ie. inbox and sent items; I noticed last night that I cannot find the package 'gLabels', which I designed a lot of my business literature in, and when I look at letters or documents I created previously, the fonts are different, and I am unable to find fonts I used previously. This is despite trying CD versions of 8.10, 9.10 and 10.04 all desktop.
 
I do hope you can be of assistance in these problems please.
 
Thank you,
 
Richard

---

### Post by mörgæs on 2010-08-09
It sounds like most of your problems are related to ownership and/or permission problems. 

There is a good and easy introduction to these topics in
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

