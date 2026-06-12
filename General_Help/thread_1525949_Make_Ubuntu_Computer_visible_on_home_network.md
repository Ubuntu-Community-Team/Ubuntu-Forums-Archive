---
title: "Make Ubuntu Computer visible on home network"
date: 2010-07-07
forum: General Help
---

### Post by bubblefish on 2010-07-07
I installed Ubuntu 10.4 today because my Windows laptop got a nasty program from some forward from a "friend." I couldn't do anything on my computer, so I installed Ubuntu over the Windows XP. (erased hard drive, complete install). Everything is great except now my wife can't print to the printers on my computer. In fact, my computer w/Ubuntu can "see" everything on her computer, but her computer can't "see" mine or the printers on it. How do I make my Ubuntu computer visible to a Windows computer on the home (MSHOME) network?

---

### Post by redfox1160 on 2010-07-07
This can be done with samba ([http://www.samba.org/]("http://www.samba.org/")).
Open the terminal and type
```
sudo apt-get install samba
```
Then you want to copy the configuration file just in-case you accidentally mess it up.
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_default
```
Next, you have to edit the config file with a text editor. You would probably use gedit:
```
sudo gedit /etc/samba/smb.conf
```
Under **Global Settings**, change the **"workgroup ="** value to equal whatever your workgroup's name is. Make a new line under that that says **"netbios = <server name>"**, but replace **<server name>** with the name of your computer. Next, go to the **Permissions** section. Under the line that says **";    Browseable = no"**, name your share by typing the following:
[B][MYSHARE]
[INDENT]comment = Myshare
path = /myshare
read only = no
guest ok = yes[/INDENT][/b]
Then scroll back up to the **Authentication** section and change the line that says **"#    security = user"** to **"    security = share"** (remember to remove the #). Save the file and go back to the terminal. In the terminal type```
sudo mkdir /myshare
sudo chmod 777 /myshare
```This creates the directory **myshare**, and changes the permissions so anyone can read, write, or execute it. Next you have to restart samba with one of the following commands:```
sudo /etc/init.d/samba restart
sudo /etc/init.d/smb restart
sudo /etc/init.d/smbd restart
```
I am not sure which one it is, but it will only let you do one of them.
Now, on your windows pc, open the **Run** dialog box and type in **"\\<SERVER NAME>"** but replace **<SERVER NAME>** with the name of your Ubuntu computer.

You should now be able to see the shared directory, and printers on the Ubuntu computer. Hope this helps!

-redfox1160

---

### Post by bubblefish on 2010-07-07
Thanks, Redfox. It almost works. The Windows computer now sees the Ubuntu computer. However, in the window that opens when I click on "my network places>entire network>samba/ubuntu computer>MyShare," there is nothing in the window. If I click on "add printer," it says I don't have privileges. If I put in my user name and Windows password, it doesn't work. If I put in my Ubuntu user name and Ubuntu password, that doesn't allow me access, either.

---

### Post by redfox1160 on 2010-07-07
The folder (myshare) will be empty unless you put something in it. The printers folder only shows printers that are on the Ubuntu computer. Are you accessing the Ubuntu computer through the Run dialog on the Windows computer?

---

### Post by bubblefish on 2010-07-08
Thanx, Redfoxx. I came to that conclusion and you confirm it. On the Windows(***&&%$&##) computer, I go to 'printers and fax' and click "add printer." I browse for printers. Now, at least, the Ubuntu computer is listed, but no printers show up. I have sharing turned on in the Ubuntu computer, and server set to broadcast printers to the net. I will see if repeated attempts to add printer eventually make the printers on the Ubuntu machine show up when I browse for printers on the Windows (***&&%$&##) machine. I am hinting to the mechanically/technology-challenged wife that she should learn Ubuntu. I almost hope her machine gets a virus so I have an excuse to over-write the OS with Ubuntu 10.4.

Thanks for your help. Progress has been made, at least in the fact that the computers see each other.

---

### Post by luceerose on 2010-07-08
If I'm understanding you correctly, the printer is attached to the Ubuntu computer?
If that's right go to System>Administration>Printing
then click on Server>Settings
Make sure the first 3 boxes are ticked.
'Show printers shared by other systems'
'Publish shared printers connected to this system'
& 'Allow printing from the internet'

It may be necessary to reboot windows for it to catch on (not sure, it's been a very long time since windows for me).
Then see if you can find the printer from windows using ipp protocol (internet printer).

---

### Post by bubblefish on 2010-07-08
Thank you, Larsenguitars. I already have checked the boxes you mentioned in the printer server settings. As soon as my wife gets done with her Windows machine, I'll get on it and see if the rebooting worked to make the printers on the Ubuntu machine visible.

---

### Post by minask2010 on 2012-06-24
That was really helpful .... thanks

---

