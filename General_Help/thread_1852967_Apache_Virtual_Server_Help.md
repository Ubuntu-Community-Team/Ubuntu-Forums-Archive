---
title: "Apache Virtual Server Help"
date: 2011-10-01
forum: General Help
---

### Post by ptmuldoon on 2011-10-01
I hope I explain this correctly...

I'm currently running 2 websites here at home on Ubuntu.

ie, [www.mysite1.com](www.mysite1.com) and [www.mysite2.com](www.mysite2.com).  

Site 1 is the default when setting up apache and points to /var/www

Site 2 I have pointing to a different location of /mnt/public/xxx/

From outside my home, I can access both sites correctly. But from here within my house, when I type 192.168.x.xx, it will load the default Site 1 only.

How would you access Site 2 from within your LAN?

---

### Post by SeijiSensei on 2011-10-01
Name-based virtual hosting means what it says; it relies on the name of the server within the URL.  If you use an IP address, it will connect to the first server in /etc/apache2/sites-enabled, which is typically 000-default on a Ubuntu box.

The best-practice solution for this is to run a name server that handles requests for the local network, but that's overkill for just a couple of client machines.  Instead edit (as root with sudo) the file /etc/hosts on the client machine and add

```

192.168.x.x    www.mysite1.com www.mysite2.com

```

Now try using [http://www.mysite2.com/](http://www.mysite2.com/) and see what happens.

---

### Post by ptmuldoon on 2011-10-02
Thanks for help.   But to help me understand better.

As I'm working to connect to from a Windows machine to Ubuntu Apache server.  Do I edit the host file the Ubuntu serve or on the Windows Client?

And do you edit the 192.168.x.x in the hosts file to the that of the server, or leave it as x.x?

---

### Post by Doug S on 2011-10-02
> Do I edit the host file the Ubuntu serve or on the Windows Client?The windows client. You will have to find the hosts file, it might be at c:\windows\systems32\drivers\etc .
>  
And do you edit the 192.168.x.x in the hosts file to the that of the server, or leave it as x.x?
 

Yes, edit it to he IP of ther server. No, do not leave it as x.x.

---

### Post by ptmuldoon on 2011-10-02
Thanks guys!   Works perfectly.

---

