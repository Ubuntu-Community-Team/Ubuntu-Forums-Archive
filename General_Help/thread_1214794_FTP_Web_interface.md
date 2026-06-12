---
title: "FTP Web interface"
date: 2009-07-16
forum: General Help
---

### Post by rnelson0 on 2009-07-16
I have a machine at home running mythbuntu which I also use to download files via FTP. A lot of times I find myself away from that computer, so I VNC into it, then start the FTP downloads.

I was wondering if Filezilla or any other FTP clients out there have a web interface in which I can start my downloads instead of having to VNC into the machine each time. 

Any idea?

---

### Post by t4thfavor on 2009-07-17
i found a few that are supposed to run on apache, and php, but none that were written in the last 7 years, and non that I got towork with php5. This is interesting, I will keep trying.

---

### Post by jonobr on 2009-07-18
actually (unless Im misreading the question) a regular browser acts as an ftp client.

In the url, you just use,

ftp://<username>:<password>@ipaddress

Some just allow you to do 
ftp://<username>@ipaddress

---

### Post by t4thfavor on 2009-07-18
They want to log into a web interface on a server, and use the browser to download ftp files onto the server running the while being able to log out of the web interface, and have fies still download, kinda like Transmissions, or utorrent web interface but for ftp. 

I found some things that do the move navigate, and delete files on a server, but nothing that can get a file from a third server. They would be easy enougn to create if you were in need enough to learn a bit of php.

One I found on sourceforge was php-ftp. Though it needed some tweaking to get running.

---

