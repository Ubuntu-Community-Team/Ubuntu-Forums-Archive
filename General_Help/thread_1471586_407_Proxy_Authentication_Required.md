---
title: "407 Proxy Authentication Required"
date: 2010-05-03
forum: General Help
---

### Post by criptommy on 2010-05-03
I have the 407 Proxy Authentication Required error when i use apt-get or when i try to install hardware drivers. Synaptic and Update manager are working perfectly working.
I have already modified apt.conf with
Acquire::http::Proxy "http://rcd:internet@172.31.100.29:3128";
Acquire::ftp::Proxy "ftp://rcd:internet@172.31.100.29:3128";
and also added the following lines to bash.bashrc
export http_proxy=http://rcd:internet@172.31.100.29:3128/
export ftp_proxy=http://rcd:internet@172.31.100.29:3128/
but the following errors are showing with apt-get
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
etc
and also when i try to install nvidia drivers the following error comes
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_195.36.08-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_195.36.08-0ubuntu2_i386.deb) 407  Proxy Authentication Required.
I have enetered proxy settings and username in Network proxy and Synaptic. Pls Help!

---

### Post by criptommy on 2010-05-04
Somebody pls help. I am using Lucid Lynx btw

---

### Post by criptommy on 2010-05-04
:(

---

### Post by Pureferret on 2010-05-18
I need the same advice! Help please!

---

### Post by criptommy on 2010-05-20
Somebody please!!!!!!

---

### Post by dino99 on 2010-05-20
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by pavithran on 2010-06-29
[SIZE=2]I had a similar problem where synaptic worked well (after entering proxy  settings, along with the authentication details, in  Settings->Preferences->Network), but apt-get gave "407  Proxy  Authentication Required". I tried this and think it is resolved:

1. Switch to root terminal and type:
    
    [/SIZE] [FONT=System][SIZE=2]export  http_proxy=http://myuname:mypass@myproxy:myport[/SIZE][/FONT][SIZE=2]

2. Open a file called apt.conf in /etc/apt/ . This file would already  have the following line if you have set the synaptic proxy settings:

    [/SIZE]  [FONT=System][SIZE=2]Acquire::http::proxy "http://myproxy:myport/";[/SIZE][/FONT][SIZE=2]

The problem here is that the authentication detail is not given, which  is the reason for the "407 Proxy Authentication Required" message.  Delete this line and type the below line, save and exit.

    [/SIZE]  [FONT=System][SIZE=2]Acquire::http::proxy "http://[/SIZE][/FONT][FONT=System][SIZE=2]myuname:mypass@[/SIZE][/FONT][FONT=System][SIZE=2]myproxy:myport/";
  
  [FONT=Arial]Additionally, you can also add the line:[/FONT]
  
   Acquire::ftp::Proxy "ftp://myuname:mypass@myproxy:myport/";[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=System][SIZE=2]
3. [FONT=Arial]now do:[/FONT]
   
   apt-get clean
  
  [FONT=Arial]After this try apt-get and it should work. It did  for me ... hope it works for some facing the same problem.[/FONT]
[/SIZE][/FONT]

---

### Post by dancil on 2010-07-01
Thanks Pavithran,

This worked for me as well!
):P

---

### Post by nawir on 2010-08-30
it also works for me,thanks :)

---

### Post by habskilla on 2011-10-07
Thanks, worked for me also!

---

