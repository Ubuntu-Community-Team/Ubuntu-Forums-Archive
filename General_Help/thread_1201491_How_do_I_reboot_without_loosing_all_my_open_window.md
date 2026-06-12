---
title: "How do I reboot without loosing all my open windows?"
date: 2009-07-01
forum: General Help
---

### Post by lightnb on 2009-07-01
I need to reboot the machine, but save everything on the desktop just the way it is.

Window positions, files that are open, ssh connections to remote machines, programs that are open, which desktop their on, everything.

---

### Post by colau on 2009-07-01
> **lightnb said:**
> I need to reboot the machine, but save everything on the desktop just the way it is.

Window positions, files that are open, ssh connections to remote machines, programs that are open, which desktop their on, everything.
I think ,it's not possible.

---

### Post by WRDN on 2009-07-01
Go to System > Preferences > Startup Applications, click the Options tab, and check the checkbox reading "Automatically remember running applications when logging out".
You can also set the startup programs manually on the "Startup Programs" tab.

---

### Post by colau on 2009-07-01
> **WRDN said:**
> Go to System > Preferences > Startup Applications, click the Options tab, and check the checkbox reading "Automatically remember running applications when logging out".
You can also set the startup programs manually on the "Startup Programs" tab.
Cool.
+1

---

### Post by apel_2804 on 2009-07-01
> **WRDN said:**
> Go to System > Preferences > Startup Applications, click the Options tab, and check the checkbox reading "Automatically remember running applications when logging out".
You can also set the startup programs manually on the "Startup Programs" tab.

But that will only start the applications after reboot. The sessions will be (of course) closed. The firefox will open all tabs/websites after restart if this option is enabled.

---

### Post by credobyte on 2009-07-01
You can save your session ( all open applications will be launched on startup - explained by WRDN ), but .. you can't save windows positioning and connections.

---

### Post by colau on 2009-07-01
> **lightnb said:**
> I need to reboot the machine, but save everything on the desktop just the way it is.

Window positions, files that are open, ssh connections to remote machines, programs that are open, which desktop their on, everything.
Probably you can't save windows position.

---

### Post by lightnb on 2009-07-01
I'm not seeing a "Start-up Applications" option. I found an "automatically remember running applications when logging out" option under the options tab of "sessions". It's already checked though, so I guess it doesn't work?

I'm running 8.10.

Here's my situation:

I administer several servers via SSH/SSHFS. So I've usually got eight virtual desktops, each with it's own file browser (of the SSHFS mount), a text editor with multiple text files open in tabs, and one or two terminals open (with SSH connections) on each desktop.

It's usually just when you get everything the way you like it that a sound or video daemon goes off the deep end, and starts blasting the same two notes over and over again like a skipping CD. (of course the volume control stops responding at the same time). Or the DVD player decides it's not going to use the green channel today, and your video will be red, blue, and purple. I have yet to find a way to "whack" the multimedia drivers and get them to work properly again without a system reboot (or at very least, an X-server restart, which still causes you to loose all open windows.

I never have to reboot my Ubuntu servers... but the desktop seems to need a reboot every two or three days for one reason or another. So I really need a way to save my session, reboot the underlying system, and then restore the session on top.

How does the window manager store the window location? In a file? In the RAM? It seems that one could simply save the position value for all open windows onto a text file, and if such a file exists on reboot, load the windows and put them back to their saved locations?

---

### Post by sedawk on 2009-07-01
Take a second machine (e.g. a server that is running 24/7 anyway)
and run a (VNC) virtual desktop on it. Then connect to it using
a VNC client and configure all your workspaces and admin terminals.
If your local desktop machine reboots or crashes or whatsover the
VNC virtual desktop stays up and running and you can connect
to it again. 
Or you can connect to it from any other system on the network.

For security you can forbid any VNC network traffic and use
a ssh tunnel or you connect to the server using ssh -X and
run the VNC client on the server itself.

vinagre is a nice VNC client.

VNC servers have startup script to start up applications after
the server crashed or is restarted.
If you use ssh authentication via known hosts you can even
reconnect to your machines automatically.

---

### Post by lightnb on 2009-07-01
sedawk, That's not a bad idea- a few questions:

1.) Can the VNC desktop be on a virtual machine? I can easily spawn new KVM/Libvirt VMs, but I've never tried making one with a GUI before.

2.) Can I run Compiz on the VNC?

---

