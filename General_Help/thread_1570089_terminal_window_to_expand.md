---
title: "terminal window to expand"
date: 2010-09-07
forum: General Help
---

### Post by averlon on 2010-09-07
Hi,
I am new to Ubuntu, not completely new to linux.
 
I have installed the Server (10.4).
The Server now shows a terminial window after start to login - this is gernerally fine.
 
The window cannot get expanded, nor can I scroll in the window for older output.
 
To be honest, I am more used to run a GUI and run a terminal within a gui. There you can scroll and also expand the window. This may be because it is a program running in x11-mode.
 
I am not realy used to run a server only from the commandline - but I will try to go this way. But still, the small window is a little bit bad to work on.
 
I should tell: I have installed the server in a virtualbox.
 
Is there a way to expand the window and make it scrollable?

---

### Post by WorMzy on 2010-09-07
You can press Shift+PageUp to scroll up, and Shift+PageDown to scroll down, but as far as I know (I'm not on Ubuntu) only a couple of pages is kept in the buffer. You can probably alter how much is stored somehow, but I couldn't tell you how you'd go about setting that. The terminal should fill the entire screen. If it doesn't, or the text is too large for your liking, then you'll need to try different vga modes. Again, I'm not sure how you'd do that, since Ubuntu uses grub2 now, which I'm not familiar with. There should be plenty of tutorials on google explaining how to do it.

You may want to consider installing gdm or kdm, and having a desktop environment.

```
sudo apt-get install gdm
```

---

### Post by JohnHeikkila on 2010-09-07
If you can't see your mouse, it's not scrollable. Don't know much about Ubuntu Server edition, but if the server edition has a GUI or Xorg server, it can be started with ```
startx
```

This article may help you if you want to install a GUI on the Ubuntu Server:
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by btindie on 2010-09-07
If you're running it under VirtualBox then it'll be running in a window under the host OS. As a start you may want to set the [VGA mode ]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers")to a higher one and run VirtualBox in full screen mode to make the most of it.
 
Failing that, you can always SSH into the host which has a similar feel to a terminal under X.

---

### Post by averlon on 2010-09-11
Hi,
thanks for the replies.
 
I would like to learn a little bit more to manage a linux server via the commandline, less with a gui.
All I know is, that working with a server on the command line is the normal way to run a server (except windows).
 
Based on your recommendations I have installed the "ubuntu-desktop", in fact gnome.
 
Now, when I start the server, it goes automatically in gui (gnome) mode, already for the login.
 
What I would like to have:
I would like to have the choice either to run the server in a commandline mode or to use a gui when I work.
 
What I would like the server to be configured:
- start server and come up with a commandline login
- after I have done the login, I would like to have a command to run temporarily a gui, either gnome or which ever.
- once I end the gui (like any other program) I would like to be back on the commandline level.
 
Could anyone give me a hint how to setup and enable my server configuration to support this ideas?
 
Where do I have to take away the automatic start of the gui in my current configuration and to enable a commandline mode at startup?
What command do I have to type to start gnome or kde to run that gui only on request, not setup a permanently config?
 
Thanks

---

### Post by btindie on 2010-09-15
Linux has various runlevels, on the majority of them 3 is the terminal and 5 is the GUI. However, Ubuntu (Debian) is a different beast alltogether. I think it boots in runlevel 2 off the top of my head.
 
I think you can have it boot straight into the terminal by appending the word 'text' to the GRUB boot options. So when you first boot your machine, select the right option, press 'e' and at the end of the line type 'text' and boot that. That should bring it up into text only mode. You may then be able to start the gui by typing startx when logged in as a regular user. If that works and you're happy with it, you can create a new GRUB entry for booting into terminal mode. You can also change the resolution/font size of the terminal window to make it easier to use. When run in terminal only mode it is of course less resource intense.
 
You don't have to have it running in terminal mode to use the console. From within the GUI you can always bring up a terminal window and use that. It then gives you the option to resize the window and have multiple terminals open. When you exit the GUI when it's started from the terminal it will automatically drop you back to the terminal.
 
From the GUI you can switch to a console windows using Ctrl+Alt+F[1-6]. It's not as 'friendly' as using a console within the GUI. To get back to the GUI press Ctrl+Alt+F7.
 
The other option is to SSH into your server from a desktop machine weather that be Linux or Win(PuTTY).

---

### Post by averlon on 2010-09-25
Hi,
where is GNOME started during startup of a server and what do i have to change to just start a terminal login without GNOME?

---

### Post by btindie on 2010-09-26
As I said in my previous post, if you edit the Grub boot options when the grub menu appears and append *text* it will boot in terminal mode. To make it permanent edit the Grub configuration file as described in the guide [here]("http://www.jghosh.net/blogs/?tag=ubuntu-lucid-disable-gdm") or [here]("http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/").
 
The alternative being to stop GDM from starting altogether, see [here]("http://blog.obsidianproject.co.uk/2010/09/disable-gdm-at-bootup-on-ubuntu-lucid.html").
 
Also take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1322949").

---

### Post by averlon on 2010-09-27
Hi btindie,
thanks for your help. It now works!
Yes, you already told me (us) what to do and in your last reply you added for me also how. This was the final help.
Thanks again.

---

