---
title: "&quot;remoting&quot; webserver from xp machine"
date: 2006-04-10
forum: General Help
---

### Post by MaZZly on 2006-04-10
hi i've set up a webserver using apache on my ubuntu server,
now i would like to be able to change files on the ubuntu machine from my xp machine
i tried setting up a share with samba:

[Hemsida]
   comment = my homesite
   browseable = yes
   path = /var/www/
   valid users = mazzly
   public = yes
   read only = no
   writeable = yes

but when i try to write to it i get some permission error.
I tried looking at the permission tab on the /var/www/ folder in ubuntu and it stood:
owner: root
group: root
(my other shares in samba are working good)


is there anyway i could access and change files on the ubuntu machine from the xp machine??




*edit* sry that i didn't put a "?" in the topic (if it matters here)
 
thnx in regards
//MaZZly

---

### Post by OffHand on 2006-04-10
FTP with CHMOD function maybe.

---

### Post by thespazzz on 2006-04-10
I have never been able to get Samba working reliably with Linux so this is what I do.

For the record the webserver is on a Fedora Machine at this point though at some point in the future I do plan to move it over to Ubuntu.

I use a seperate user account setup to allow both FTP access and SSH access.  You can link the /var/www/whatever directory to your home directory to get quick access to it from your FTP account.

Then whenever you need to do any "under the hood" type work you can use a program called "Putty" to login to your box using SSH and work on the command line.  You can also use Putty with another program (though I forget the name if it, its basicly an X server for windows) that will also allow you to get an X session started by remote so you can work from the GUI by remote.  Though I found that to be somewhat less than stable.

---

### Post by pete on 2006-04-10
Mazzly, I aggree with thespazzz that ssh and/or ftp is probably the better way to go (I use ssh myself).

That being said, have you added the smb user on your Ubuntu box via smbpasswd?

---

### Post by MaZZly on 2006-04-11
ofcourse i have put the user mazzly using the "smbpasswd" command
else my other samba shares would not work correctly

i can use the ubuntu machine from my xp machine using "remote desktop"(ubuntu) and tightvnc(xp)
but i would like to work on the homesite from my xp machine, becouse the ubuntu machine is a bit slow to work with ;)

thespazzz, could u explain more how to do that and what to do, like apt-get and things like that?
or is there a guide

sry for my wierd english :)


*EDIT* found the solution in the forums, here it is:
sudo chown username /var/www/ -R
that gives the "username" user acces to the folder, YAY!!

---

### Post by MaZZly on 2006-04-11
New problem:
i dont get my index.htm showing
if i connect to 192.168.0.1 i see the content of the /var/www/ folder, but when i click for example index.htm it says:
**Forbidden**
You don't have permission to access /index.htm on this server.

i can only go into the apache2-default folder where i see an apache2 page

its the same if i connect [http://localhost](http://localhost) from my ubuntu machine

---

### Post by thespazzz on 2006-04-11
How are your permissions set on the folder that contains the Index.HTML file.

Who ones it, what group is it in and what is its actual permissions.

---

### Post by MaZZly on 2006-04-12
nvm about the problem, got help in another thread, only problem now is that i cant connect to my homesite by using my ip , works if i connect trough local ip
and yes, port 80 is open

---

### Post by alamba on 2006-04-12
Mazzly: With regard to your original thread you might want to make sure that the user u're using for samba "mazzly" has permission on the folder you're trying to open.

As far as FTP is concerned, I'll recommend you use SCP which is installed with the same package as ssh and doesn't transmit your username and passwd in clear text.

As far as the forbidden web page issue is concerned you'll need to look into the permission of the index file. I should be readable by the apache user.

What error do you get when opening your site by IP? Post a traceroute to check if you're able to reach the IP.

A

---

### Post by MaZZly on 2006-04-12
i get a blank page (if use internet ip)
it works if i use the local ip

how to traceroute?

---

