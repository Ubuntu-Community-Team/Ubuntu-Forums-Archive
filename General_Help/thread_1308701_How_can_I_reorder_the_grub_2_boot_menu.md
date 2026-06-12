---
title: "How can I reorder the grub 2 boot menu?"
date: 2009-10-31
forum: General Help
---

### Post by Chris0134 on 2009-10-31
Hello all, 

An absolute beginner here, just got on the Linux train.  Tried Jaunty a week ago; first ever linux experience.  I've now upgraded to Karmic (technically i did a clean install.) 

My question: How do I reorder the new grub so that I can put my Vista OS first; so that it will be selected automatically, when microsoft issues another of the many updates requiring restart?

The grub loader is now quite complex, and I have yet to make true sense of any other posts pertaining to the subject.  Can someone please post an idiot-proof, step-by-step for this process?

---

### Post by cariboo on 2009-10-31
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1308669"), the poster had the same problem.

---

### Post by mxcrowe on 2009-10-31
Yes, I posted that thread and seemed to be on the right track, but cannot get the boot order change to actually work!

---

### Post by wilee-nilee on 2009-10-31
Install startup manager from synaptic or the terminal it will allow you to change the boot order.

---

### Post by drs305 on 2009-10-31
One way to do it would be to make a custom file, place the OS's in the order you want, and then name it 06_custom so it appears at the top of the Grub 2 menu list.

The custom file would go in /etc/grub.d and must be executable.  There is a sample 40_custom folder there. Copy menuentries from /boot/grub/grub.cfg to this file in the order you want them. Save the file as /etc/grub.d/06_custom, and make it executable. Then run "sudo update-grub" to incorporate it in the menu.

See this section of the Grub 2 community doc for more details:
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries")

---

### Post by Chris0134 on 2009-10-31
Alright, here it is, nice and easy... just like what the guy above said....

1 open /etc/grub.d/**30_os-prober** with root privleges in gedit.... type *sudo gedit *in the terminal and open the file.

2 save as 06_**os-prober**

3 now remove the leftover **30_os-prober**  .... it will still be there.. type *cd/etc/grub.d*.    type *rm **30_os-prober***

4 type [I]update-grub

[/I]that should do it... 

i'm sure you could just rename it using commands as well, i don't know them... I'm totally new to linux.  


[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202") -read this if you want to actually know what ur doing

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml) -read this to learn basic commands.

edit... if that doesn't work you must make the new file executable... I don't know if it retains that property after the save as... to make executable.... read the above grub 2 web page... it gives the command in the custom files section... i did it before even trying to reboot, so i don't know if it was necessary or not..

---

### Post by mxcrowe on 2009-11-01
I'm not sure what could be easier than Willee-Nilee's answer above.  I installed the startup manager and it made the whole process easy.  Other documented approaches did *not* work.  I'm sure your process works, Chris, but the startup manager is a snap and offers other features too.

---

### Post by Chris0134 on 2009-11-01
yea... I skipped right past that reply... start up manager is all ya need.

---

### Post by wilee-nilee on 2009-11-01
The funny thing about Ubuntu is that you can totally avoid all the file manipulations on the basic system with a few extra packages like the startup manager and Ubuntu Tweak, I know probably 5-10 command line inputs from memory and just remember what I need after 3 years of using Ubuntu I started on Dapper. Ubuntu really is a plug and play non geek hardware that can be modified by a geek to do even more amazing stuff, all without the usual dangers on the net. I can install and have it up in running in less then 4 hours.

---

### Post by mxcrowe on 2009-11-01
Thanks again, Willee!
Can you suggest any other crucial packages like "Startup Manager" and "Ubuntu Tweak"?  I'd like to get them installed and save myself a lot of command line headaches.

---

### Post by wilee-nilee on 2009-11-01
> **mxcrowe said:**
> Thanks again, Willee!
Can you suggest any other crucial packages like &quot;Startup Manager&quot; and &quot;Ubuntu Tweak&quot;?  I'd like to get them installed and save myself a lot of command line headaches.

 At the moment I can't remember everything but I will see if any thing comes to mind.

---

### Post by wilee-nilee on 2009-11-01
You could try gnome-do it can be enabled from ubuntu tweak then installed in UTweaks add remove. there is also a gnome-do ppa I believe, but there are changes so the easiest is probably the Ubuntu Tweak method. Gnome-do might even be in synaptic or the new software center but the UTweak version is the latest and I think actually gets you the PPA and key installed

---

### Post by Geoff_L on 2010-02-23
> **wilee-nilee said:**
> Install startup manager from synaptic or the terminal it will allow you to change the boot order.
Sorry to resurrect an old thread but I've just installed Karmic with Windows XP on my wife's laptop and need to tidy up the boot menu. Using startup manager, I can change the default OS but can't find a way to change the boot order. I've tried all I can think of but can't find that option. Am I missing something here?

For info, I installed Startup Manager with *sudo apt-get install startupmanager* and *grub-install -v* reports 1.97~beta

TIA.

Geoff

---

### Post by drs305 on 2010-02-23
> **Geoff_L said:**
> Sorry to resurrect an old thread but I've just installed Karmic with Windows XP on my wife's laptop and need to tidy up the boot menu. Using startup manager, I can change the default OS but can't find a way to change the boot order. I've tried all I can think of but can't find that option. Am I missing something here?

For info, I installed Startup Manager with *sudo apt-get install startupmanager* and *grub-install -v* reports 1.97~beta

TIA.

Geoff

By "change the boot order" do you mean the order the items appear in the menu, or which one boots by default?

To change the order the menu entries are listed, the easiest way is to construct a custom menu. Here is a good guide by meierfra. for creating a custom menu: [_Write a Custom Menu_]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

To change the boot order, you can do so with help from this thread:  [_Grub 2: 5 Basic Tasks_]("http://ubuntuforums.org/showthread.php?t=1302743").

---

### Post by Geoff_L on 2010-02-24
drs305: Thanks for the reply. I might give creating a custom menu a go later. However, I suspect that I'd need to manually edit the custom menu to reflect each kernel change and perhaps there'd be bigger issues when the system is upgraded to Lucid Lynx? If so, I might be better off just changing the default to "saved" (so that she'd boot the last used OS if she didn't make an explicit selection) and leave tweaking the Grub menu alone for now.

Edited to add: I've just created a custom menu and while doing that I noticed the use of the links /vmlinuz and /initrd.img for the last installed kernel. I've done likewise, which should mean my misgivings about having to edit the custom menu at each kernel update are unfounded.

Many thanks for the solution.

Geoff

---

### Post by drs305 on 2010-02-24
> **Geoff_L said:**
> Edited to add: I've just created a custom menu and while doing that I noticed the use of the links /vmlinuz and /initrd.img for the last installed kernel. I've done likewise, which should mean my misgivings about having to edit the custom menu at each kernel update are unfounded.

Many thanks for the solution.

Geoff

Yes, the /vmlinuz and /initrd.img "links" work very well in a custom menu. That solves the kernel update issue in Ubuntu custom menus and since Windows entries generally don't change, it's a pretty good solution.

---

### Post by cparke on 2010-10-29
The proper way is to create and re-order the prefix number on the files in the /etc/grub.d directory as needed.  For example, you'll see memtest86+ has its own separate entry...

---

### Post by €ndr! on 2011-07-04
old post bur helped me a lot. Startup Manager is the shortest and easiest way . Thank you [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")

---

