---
title: "help how instal vnc server by putty (ssh)"
date: 2011-07-23
forum: General Help
---

### Post by thxyou on 2011-07-23
hi i buy a dected server and i want control my server with UltraVNC Viewer
the company host is give me just user name is root and password of ssh
and when i ask him to instal for me vnc server he say sorry man i dont suport softwer

so can you help me how instal vnc server by putty (ssh)

---

### Post by galvatron408 on 2011-07-23
First thing you want to do is log in as your root account, create an account for yourself with sudo privilege and then lock out the root account.

Second thing you want to do is, install the vnc server so you'll want to do "sudo apt-get install vnc4server"

Once you have your vnc4server setup, then just connect to it!

Come to think of it, why do you need vnc anyway? You can do everything using SSH.

---

### Post by thxyou on 2011-07-23
> **galvatron408 said:**
> First thing you want to do is log in as your root account, create an account for yourself with sudo privilege and then lock out the root account.

Second thing you want to do is, install the vnc server so you'll want to do "sudo apt-get install vnc4server"

Once you have your vnc4server setup, then just connect to it!

Come to think of it, why do you need vnc anyway? You can do everything using SSH.

i conect with putty 
and i intal vns server with this command 
"sudo apt-get install vnc4server"
and i start the server with s command 
"vncserver"

and he ask me to setup a passworld i creat a passworld

and now i try to conect with UltraVNC Viewer

and i see this White screen 
[IMG]http://data.imagup.com/11/1126116446.JPG[/IMG]

i want see the desktop

so i try this comand 
vim .vnc/xstartup
to add this exec gnome-seddion &

but i cant  i am stuck her  i dont know how add this line exec gnome-seddion &
[IMG]http://data.imagup.com/12/1126116990.JPG[/IMG]

---

### Post by thxyou on 2011-07-23
now finly after 1 hor try add this line 

how save the file now 

[IMG]http://data.imagup.com/10/1126120942.JPG[/IMG]

i sersh in google and i find this key :wq
so what buton i prese to save this line 

i am crazy now

---

### Post by galvatron408 on 2011-07-23
Press esc and then press shift+: and then type wq! And press enter

---

### Post by thxyou on 2011-07-23
> **galvatron408 said:**
> Press esc and then press shift+: and then type wq! And press enter
ok now  i save  the file 
[IMG]http://data.imagup.com/11/1126124826.JPG[/IMG]


and wen i try conect with UltraVNC Viewer i see this scren 
[IMG]http://data.imagup.com/11/1126124906.JPG[/IMG]

so what  i do now

---

### Post by thxyou on 2011-07-24
help me

---

### Post by thxyou on 2011-07-24
so no help

---

### Post by galvatron408 on 2011-07-24
Yes, that means vnc server is working. So, it sounds like you either don't have the desktop installed or you're just in the wrong init level (or both).

Ok, at the SSH prompt, type this...

sudo apt-get install ubuntu-desktop

When, you're done, if you still don't see the desktop, type this...

sudo /sbin/init 5 

After typing this, you might not see anything but use your vnc client to connect and you should see the difference if it worked.

(init levels are 0=shutdown, 1=single user mode, 2=multi user mode without networking, 3=multi user mode with networking, no desktop, 4=reserved, 5=multi user mode with the desktop, 6=reboot)

Obviously, you want to avoid run level 0,1,2,4,6 unless you really want to shut things down or reboot.

---

