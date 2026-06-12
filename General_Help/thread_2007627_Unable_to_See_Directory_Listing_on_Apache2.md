---
title: "Unable to See Directory Listing on Apache2"
date: 2012-06-21
forum: General Help
---

### Post by jacobroecker on 2012-06-21
Bear with me folks I have a slightly unusual setup.

I'm running U10.04 Desktop and have installed Apache to allow my iOS devices to view some video files.  Apache is working fine and I can see the directory structure using browsers on other machines, but Safari on the IOS is not seeing it.

When I view the directory listing of my wp-site (hosted on an apache server) the iOS devices can see it fine.

I've got httpd.conf setup with the following:

<Directory /media/Movies>
Options Indexes FollowSymLinks
</Directory>

and .htaccess has:

Options Indexes

What am I missing?  I just installed Apache2 today and I'm new at this.

Thanks in advance.  

Oh, and if there's an Apache Forum that would be better to post this at, please send the URL.

---

### Post by SeijiSensei on 2012-06-21
Does Safari report an error like "access denied" or "directory index forbidden"?  What do you see in /var/log/apache2/error.log when you try to connect with Safari?

---

### Post by jacobroecker on 2012-06-21
iOS Safari gives me a "Cannot Open Page" Safari could not open the page because the server stopped responding.


There is no corresponding error message in the error.log file.

---

### Post by SeijiSensei on 2012-06-23
No entry in the logs suggests the iOS devices cannot see the server over the network.  Can you install anything like a telnet application?  If so, you could try telnetting to the server's port 80 and see if you can connect.

I [searched Google]("https://www.google.com/search?q=nmap+ios") to see if there is an iOS version of the extraordinary scanner called [nmap]("http://insecure.org/nmap").  I don't see a native app for iOS from [Fyodor]("http://insecure.org/fyodor/") himself, as it's pretty likely you'd need to root your phone.  As a security precaution, all the cool stuff in nmap requires root privileges.  You can ping-scan a network as an ordinary user; comes in handy sometimes.

I take it you can ping the IP address on the iOS device from the web server after the phone, pad, etc. is connected?  I know nothing about iOS, but I'd think that if you cannot ping the phone, then all other bets are off.  Can you open a terminal application on the phone and run common applications like ping?  If so, can you ping the server's IP address?

Next, have you tried using an IP-based URL like [noparse]http://192.168.1.1/[/noparse] instead of a symbolic hostname?  What happens?

---

### Post by jacobroecker on 2012-06-23
I went through just about everything I could think of and it turns out the problem was at my router.  It's one of the less expensive ones out there and would get hung up trying to connect the server to its wireless clients.  After a complete factory reset and a network reset on the iOS devices they started working.  The router will get upgraded on payday since it has proven unreliable.

Thanks for your help.  I've learned a lot from troubleshooting this and appreciate it.

---

