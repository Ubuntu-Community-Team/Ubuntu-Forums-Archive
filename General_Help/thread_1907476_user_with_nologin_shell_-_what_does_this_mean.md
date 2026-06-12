---
title: "user with nologin shell - what does this mean?"
date: 2012-01-11
forum: General Help
---

### Post by mbuell on 2012-01-11
This turned into a rant, but started as "Could somebody please translate?"

From [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html")
> To allow users with a shell of /usr/sbin/nologin access to FTP, but have no shell access, edit /etc/shells adding the nologin shell: 
I think a shell is an instance of somebody or something logging in to my computer. But next it lists all the places where shells are - why are there so many shells in so many different places? And WHO are "users with a shell of /usr/sbin/nologin"? If they aren't users on my computer, how could they get a shell? 

I can google shell and get a good explanation here: [http://www.freeos.com/guides/lsst/ch01sec07.html]("http://www.freeos.com/guides/lsst/ch01sec07.html")

And I can google "What is nologin shell" to get this:
[http://www.cyberciti.biz/tips/howto-linux-shell-restricting-access.html]("http://www.cyberciti.biz/tips/howto-linux-shell-restricting-access.html")

Also pretty good. 

I tell ya what, if I really thought I understood this well enough, I would go and edit that help page if I could. I don't think I should have to be googling and chasing pages every 3rd word. 

And it continues in the same incomprehensible vein:
> This is necessary because, by default vsftpd uses PAM for authentication, and the /etc/pam.d/vsftpd configuration file contains:

auth    required        pam_shells.so

The shells PAM module restricts access to shells listed in the /etc/shells file. 

Try this instead:
> To allow users to use ftp but not login to the computer, you need to make their default shell be a nologin shell. This allows them access to ftp, but denies them the ability to login. Since vsftpd uses PAM authentication, the nologin shell needs to be listed in the shell list for PAM [ /etc/shells ]. If PAM does not find a shell there it won't allow access. 

Something like that. THEN put in the detail of the long list - or maybe not. 

Note - this is from the official documentation - not an open wiki. So, official documenters, please take note. Thanks for your time.

---

### Post by mbuell on 2012-01-14
I'm following up on my previous post. I still thing the official doc wording is the pits - but I have more to add that is pertinent. 

I put a description of some of the story here: 
[http://ubuntuforums.org/showthread.php?p=11610739#post11610739]("http://ubuntuforums.org/showthread.php?p=11610739#post11610739")
Not wanting to double post, I set this link. 

But here is the nut - nologin is probably NOT secure. After finding references that seemed to indicate it WAS secure, I started hitting references that indicated it was NOT secure. The guys writing this stuff are way deeper in the bedrock of things than I am - so I came back to this:

Vsftpd was written with security as the top priority. Ubuntu was put together, and my understanding has always been that Ubuntu regards security as a top priority. Vsftpd sets the default to using anonymous ftp. The people discussing the insecurity of a nologin user were fixing it by undoing Ubuntu defaults. I decided to stick with the path of the people I trust more  - go with the vsftpd and Ubuntu defaults.

---

### Post by Lars Noodén on 2012-01-14
Correct me if I am wrong, but from what I gather vsftp does not support actual SFTP.  

If that is the case, then you might be interested in these pages:

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

[http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

---

### Post by mbuell on 2012-01-15
> **Lars Noodén said:**
> Correct me if I am wrong, but from what I gather vsftp does not support actual SFTP.  


Hmmm - I've closed a lot of pages, but I think I saw one that addressed this issue, and I think vsftpd DOES offer sftp. 

From what I read before, I was thinking that sftp did not offer anything particularly superior for user authentication - but from one of your links, it would seem that it can be just as secure as what I will do for my ssh - using key-based login. 

I did this little ftp exercise as just that - an exercise, and it won't be something I keep going. I can make ssh available and more secure, and since any normal access through my firewall would only be for myself, it will do. This got started because I forgot to take a cd to a meeting for a friend, so I thought this might be a useful way for them to get the data. Eventually it was easier to drive across town with a cd. I learned something, but I'm not sure it was worth the effort.

---

