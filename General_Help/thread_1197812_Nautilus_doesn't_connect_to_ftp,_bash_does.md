---
title: "Nautilus doesn't connect to ftp, bash does"
date: 2009-06-26
forum: General Help
---

### Post by Deeg on 2009-06-26
Hi,

I am trying to set up an ftp connection with Nautilus, but it won't connect "Sorry, couldn't display all the contents of "/ on server": Could not connect to host". The funny thing is that when I use ```
ftp server
``` in bash, it does connect.

It seems to be server-related, because I can connect to other ftp servers using Nautilus.

Can anybody help troubleshooting here? For example where can I find Nautilus error messages?

Cheers,
deeg

---

### Post by clonne4crw on 2009-06-26
I've never had that problem before when I just put the address of the server into the address bar of Nautilus. Is that what you're doing?

---

### Post by Deeg on 2009-06-27
I've tried the address bar, with and without password and also Connect to server, both are unsuccessful!

---

### Post by fragos on 2009-06-27
Works fine for me. I've made them bookmarks. Try the following with your own parameters in the Location: bar.

ftp://{server user}@ftp.{domain}/{folder}

You should be prompted for passwords.

---

### Post by Deeg on 2009-06-29
I have tried that, and it works for another ftp server, but not for the one I want to connect to. Therefore, it seems to be server-related, so I was looking for debugging mode in nautilus or something.

---

### Post by jeroenbest on 2011-02-23
I have set up my own FTP server. Connecting to it via(command line) ftp works fine. But indeed, if I connected to it using Nautilus I also got the error: "Sorry, couldn't display all the contents of "/ on server": Could not connect to host".

Since my server is behind a router I had to apply port forwarding. However, in my case I also had to setup the default server. So port forwading should be enabled and putting the default server correctly.

I hope this will help you...

---

