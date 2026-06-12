---
title: "Ubuntu update"
date: 2011-11-14
forum: General Help
---

### Post by piosif on 2011-11-14
I just updated to Ubuntu 11.04, and I think everything went well, but now that I try to open it, I cannot, because on the main desk there is no Menu bars, neither on top nor on the bottom. I cannot do anything to enter my computer. Can somebody please tell me what to do?

---

### Post by sarton85 on 2011-11-14
Did you try a reboot to see what happens?

If a reboot doesn't work to bring the panels back, reboot your computer until the login screen and select Ubuntu Classic Desktop from the menu below; [http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

Please let us know if that worked.

---

### Post by piosif on 2011-11-14
Thanks for your answer. 
I have tried to reboot many times now, but when I do so, there is no option to enter the Classic Ubuntu. I can only enter a previous version, but when I do so, I end up with the same problem... no menu bars.
With a right click I can manage to change and personalize the desk top, but nothing else.

---

### Post by sarton85 on 2011-11-14
> Thanks for your answer. 
I have tried to reboot many times now, but when I do so, there is no  option to enter the Classic Ubuntu. I can only enter a previous version,  but when I do so, I end up with the same problem... no menu bars.
With a right click I can manage to change and personalize the desk top, but nothing else.     Strange that you cannot change to Ubuntu Classic as explained in the link. When you are in the login screen, first click your name. Before you click your name, the menu to switch to Ubuntu Classic is not visible. But maybe you tried this already.

You say that you can personalize the desktop by right clicking. That tells me that you still have some control and that Nautilus maybe didn't start the way it should.

What you can try is to press ALT + F2. A command box should come up. Type the following in the box;

```
nautilus
```and press enter.

Let me know what happens.

---

### Post by sarton85 on 2011-11-14
Also try ALT + F2 and type;

```
gnome-panel
```

---

### Post by piosif on 2011-11-14
No nothing. I have tried Alt with all the Fs and nothing happens. Only when I press F1 alone. a Ubuntu Desktop Guide window pops up, which gives me much information about Ubuntu 11.04, but with no commands so as to be able to do something.

---

### Post by piosif on 2011-11-14
I forgot to mention another thing I am able to do, and that is when doing a right click, a small menu appears, and one thing I can select is to open up the script folder. Doing so permits me to enter all my archives in the computer.
I just saw there that I can also enter a folder of "nautilus-scripts". When I open that up I have two more options:
MakePlymouth, and
MakeXsplash.
Which of the two should I select?

---

### Post by sarton85 on 2011-11-14
> I just updated to Ubuntu 11.04Did you update from Ubuntu 10.10? And what desktop environment did you use there? Gnome? I am asking because the options you mention in the right click menu shouldn't be there in the Gnome desktop. I also don't know which script you should select and if it is going to make any sense to select them.

Do you have a possibility to make a picture of your desktop with the right menu clicked so it is visible and to upload it here?

Also because I think you updated from an earlier version of Ubuntu, I think your system might be broken. But if you upload a picture of your desktop it is easier for me to analyse.

> I forgot to mention another thing I am able to do, and that is when  doing a right click, a small menu appears, and one thing I can select is  to open up the script folder. Doing so permits me to enter all my  archives in the computer.In the normal Gnome right click menu there is an option to create a launcher for applications. Do you have it? If you have this option, I would recommend to add a Terminal launcher to  your desktop. But if you don't have it, what I am writing below will  not work.

You should get a window similar to this; [http://silveiraneto.net/wp-content/uploads/2011/02/window_add_custom_application_launcher_to_gnome_panel.png](http://silveiraneto.net/wp-content/uploads/2011/02/window_add_custom_application_launcher_to_gnome_panel.png)

Fill in for Name: Terminal and for Command: gnome-terminal and click OK. You should now have a terminal launcher on your desktop.

Open it and type; gnome-panel

It should start your panels.

---

