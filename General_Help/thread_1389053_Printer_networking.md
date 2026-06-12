---
title: "Printer networking"
date: 2010-01-23
forum: General Help
---

### Post by thegreatpenguin on 2010-01-23
Hey everyone I need a little help I am trying to setup so my wifes windows pc can use my printer on ubuntu I have went in and opened up port 631 under ip 192.168.5.4 per ubuntu instructions.
sudo ufw allow proto tcp to any port 631 from 192.168.5.4
sudo ufw allow proto udp to any port 631 from 192.168.5.4then it says to go to printer setup on the windows pc and use the example below 
http://<hostname>:631/printers/<printername> replacing the host name with the pcs host name it is keith-desktop so it should read 
[http://keith-desktop:631/printers/-2600-Series](http://keith-desktop:631/printers/-2600-Series)
does this look correct or am I missing something because this wont work
any help would be appreciated,
[&#9660; Queue Name &#9660;]("http://localhost:631/printers/?QUERY=&WHICH_JOBS=&FIRST=%7BFIRST%7D&ORDER=dec")DescriptionLocationMake and ModelStatus    [-2600-Series ]("http://localhost:631/printers/-2600-Series")Lexmark  2600 Series keith-desktop Lexmark 2600 Series, 1.0Idle

---

### Post by thegreatpenguin on 2010-01-23
Ideas anyone does that look correct or am I missing something thanks.

---

### Post by thegreatpenguin on 2010-01-23
Grrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr

---

### Post by flabdablet on 2010-01-24
It's unusual for a printer name to start with - instead of a letter; are you sure that's right?

If you open a cmd window on the Windows box and type **ping keith-desktop** do you see responses?

*I thought this was a community guess I was wrong*

Might want to check your dictionary, there, champ - "community" does not mean "army of slaves at your beck and call".

---

### Post by thegreatpenguin on 2010-01-24
when doing that in a cmd promt on the windows pc i get could not find host keith-desktop check the name and try again. When I do hostname in a terminal window it says the host name is keith-desktop and the -2600-Series is what is listed under admin in cups for this printer.

---

### Post by HereInOz on 2010-01-24
Try using the ip address of the Ubuntu box rather than the host name. 

Or you could add an entry into your /etc/hosts file to that effect, to tie the host name to the ip address.  Make sure that your Ubuntu box has a static IP, otherwise confusion will reign supreme.

I also notice that you have used the host name of both desktop-keith and keith-desktop in your posts.  I will leave this one to you to check.

Cheers,

Alan

---

### Post by HereInOz on 2010-01-24
Nice reply - perhaps read the forum code of conduct.  

Having said that, I need to correct something I wrote in my last post.  I mentioned putting an entry in the /etc/hosts file, but of course, the hosts file you would be using is the one on the Windows machine, and that would be:

C:\Windows(or whatever your systemroot folder is)\System32\drivers\etc\hosts

Sorry for misleading you.

---

### Post by steveneddy on 2010-01-24
> **thegreatpenguin said:**
> That wasnt meant for you it was for the other idiot that posted earlier I am a mod on several forums and have read the rules but enough of that ive been at this for over 13 hours straight and am getting a bit pissed sorry I cant get my wife to switch to linux so I have to get this printer working to get her to shut her mouth thanks.

You need to chill out.

We don't care how many forums you supposedly are a mod on, the reason you aren't getting much help is your attitude.

I suggest that you change or erase those posts and stop calling everyone names.

We are all here as volunteers. If you don't get an answer here after 24 hours, then you may bump. You may also try Google.

******************************* ** ** *

Most modern printers have an Ethernet port on them to sit directly on the network. This printer does not I suppose?

---

### Post by HereInOz on 2010-01-24
But did my suggestion work?

---

### Post by thegreatpenguin on 2010-01-24
[QUOTE=steveneddy;8715259]You need to chill out.

We don't care how many forums you supposedly are a mod on, the reason you aren't getting much help is your attitude.

I suggest that you change or erase those posts and stop calling everyone names.

We are all here as volunteers. If you don't get an answer here after 24 hours, then you may bump. You may also try Google.

******************************* ** ** *

---

### Post by efflandt on 2010-01-24
Can the Windows box see your Linux box in network places?  Is your workgroup in /etc/samba/smb.conf the same as the workgroup on the Windows box?  Otherwise you may need a hosts entry on the Windows box or use the IP of the Ubuntu box.

Another possible issue is that built-in browser search, built into a browser can get in the way, and may assume that a name without dot is a search string.  Not sure if that is an issue for Windows internet printing, but it seems to use IE for a lot of things.  For example when I tried to enter http://efflandt-64:631/ in Firefox on my Ubuntu box, it said it could not find http://**www.**efflandt-64**.com**:631/

I was able to access it on the same PC by going to http://127.0.0.1:631/

If you go there, under the Adminstration tab are check boxes for "Share printers connected to this system" and optionally "Allow printing from the internet" (best to require username and password if you allow that).

Instructions in cups url itself says to use **http://*ip-address-or-hostname*:*port-number*/*resource*** where resource would be the queue (printer) name.  So maybe having an extra ***/printers*** in the path might throw it off unless Ubuntu does something non-standard with cups.

I have a network printer (Lexmark C543dn), so I cannot test this on a directly connected printer.  But long ago as a test I was able to print to a Linksys switch/printserver from WinXP using http://static_ip_address:631/L1 (L1 was its default/first logical queue to parallel connected hplj4l).

---

### Post by steveneddy on 2010-01-24
enjoy.....

:popcorn:

---

### Post by steveneddy on 2010-01-24
Please look here:

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by cariboo on 2010-01-24
I think the op may be better off taking a bit of time off. this thread is closed for 24 hours.

---

