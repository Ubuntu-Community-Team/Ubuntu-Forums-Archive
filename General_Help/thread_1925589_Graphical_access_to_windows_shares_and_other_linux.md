---
title: "Graphical access to windows shares and other linux machine"
date: 2012-02-14
forum: General Help
---

### Post by susja on 2012-02-14
Hello,
I have 2 notebook. One notebook runs Redhat 6.2 and another one runs Ubuntu 11.10
On RedHat machine I use Nautilus in order to access Windows shares or other Unix machines.
On Ubuntu when I start Nautilus it brings me File manager but it does not give me the option to connect to remote server ( like it does on Rhat ), is it likely different version or something else.
Could someone tell me how do you guys access remote shares on Windows or other unix system using GUI?
Thanks,

---

### Post by x1a4 on 2012-02-14
You need to specify the protocol and login info in the address bar of the file manager.  For windows, if you're using SMB, that's something like this:  

smb://WINDOMAIN;username@int.ernal.ip.add.ress/

You can also use Gigolo (it's in the repositories).  Make sure you have all appropriate subsystems (smb, nfs, etc.) running as Gigolo is just a GUI for them.

---

### Post by susja on 2012-02-15
hi x1a4,
Thanks a lot for explanation. It was really easy ( when you know :) )
It might be some syntax to use but I noticed that just placing smb://<machine_name or ip> will bring up authentication dialog and then will allow to access windows machine.
I assume that in order to access unix machine I could use similar sftp://<machine_name or ip>

Thanks again
susja

---

### Post by susja on 2012-02-15
I'm sorry to ask this 'stupid' question again but I don't see address bar in my 'File Manager', how could I get it?

---

### Post by x1a4 on 2012-02-17
In Nautilus: Go > Location

If your network is setup correctly you should have a link named 'Browse Network' in Nautilus' sidebar.  Also, entering: network:/// in the address bar should show your network.

If you don't see your network in Nautilus on Ubuntu the way you can in Red Hat that means that something is not installed.  Install Samba, UFS, etc to be able to access your network.

---

### Post by susja on 2012-02-17
Well I don't see address bar in Nautilus but I do see it in Gigolo and I could access remote Windows and Linux systems.
 I think I could leave with that i.e. browse local stuff using Nautilus and browser remote system using Gigolo.
Thanks for explanation.

---

### Post by x1a4 on 2012-02-17
When you click 'Go' on the menu, then 'Location...' in the 'Go' menu the path bar will change into a location bar.  Alternativelly, Ctrl+L should work.   

Or are you not using Nautilus?  Which file manager are you using?

---

### Post by susja on 2012-02-17
well ... on my Rhat machine I definitely use Nautilus and I don't have any issues with navigation.
On my Ubuntu machine I use File Manager which was part of the system i.e. I didn't install anything additionally. Even more ... when I execute /usr/bin/nautilus on Ubuntu it starts that File Manager. The point is that it does not have any kind menu options and the only thing that I could do inside it is either minimize/maximize or close it. I also could definitely navigate local structure inside it ... but no any menu or etc.
Using Gigalo I do have all menu options.
Well based on that I assume that File Manager that came with default Ubuntu install is Nautilus but without options to modify anything other than just navigate.
Regards

---

### Post by x1a4 on 2012-02-17
Try Alt+M to toggle the menu bar.


To enable the location bar without using the menu:  

Install **dconf-tools** then run **dconf-editor** and the setting will be found in: 

org &#10140; gnome &#10140; nautilus &#10140; preferences &#10140; always-use-location-entry

---

### Post by susja on 2012-02-18
Hi x1a4
Thanks for your help. I installed dconf-editor and now each window on my workspace has a corresponding menu bar at the very top of the screen. Now interface is similar to one I have on RedHat. I unistalled Gigolo and Ii am all set now.
Thanks again.
susja

---

### Post by Morbius1 on 2012-02-18
>  I unistalled Gigolo and Ii am all set nowYou might want to reconsider that decision. Gigolo is more that a network browser as it allows you to bookmark ( which you can also do in Nautilus ) but also to automount that remote share at login. It's even smart enough to wait until the remote machine is available before it tries to mount it's shares. It may not apply to your specific situation but it's worth considering:

[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by susja on 2012-02-18
Thanks,
that's not apply to my needs but it's worth to know

---

