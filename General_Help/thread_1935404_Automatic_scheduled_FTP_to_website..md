---
title: "Automatic scheduled FTP to website."
date: 2012-03-04
forum: General Help
---

### Post by wildbillkelso1941 on 2012-03-04
Hi all.

I am looking to transfer or update an image file to a page on my website, say every 5 minutes. I detect meteors and the software outputs a screen capture with a fixed name. I would like to refresh this automatically on the web page. I think I can do this with cron but have no idea how.

Any help or ideas would be greatly appreciated.

Many thanks.

Tim

---

### Post by llamabr on 2012-03-04
[http://superuser.com/questions/144198/how-to-create-a-cron-job-to-upload-files-to-an-ftp-server](http://superuser.com/questions/144198/how-to-create-a-cron-job-to-upload-files-to-an-ftp-server)

---

### Post by Lars Noodén on 2012-03-04
You can do this with either [sftp](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sftp.1.html) or [scp](http://manpages.ubuntu.com/manpages/oneiric/en/man1/scp.1.html) using keys made by [ssh-keygen](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keygen.1.html).  You can find dozens of HowTos on copying files without a password.  Here's one example:
[http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/)

Most use the approach where an empty passphrase is used, that's one way.  Another way is to use an agent to hold the key and reuse it.  

Staying away from FTP would be a good idea because it is so insecure that it will eventually cause a compromise.  SFTP is the safe way.
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by wildbillkelso1941 on 2012-03-06
Apologies for the delay in replying both.
Many thanks for the useful links and information. I will look into it further. Still not sure what I am doing yet, but will read up on it and learn when I have more time.

Thanks again.

Tim

---

### Post by Lars Noodén on 2012-03-07
If the image is big but does not change much then [rsync](https://help.ubuntu.com/community/rsync) might also be an option.

---

### Post by Khayyam on 2012-03-07
For cron you would do something like the following:

```
*/5 * * * * /path/to/script.sh
```

"script.sh" could then be a simple oneliner to scp/sftp you image to your webserver.

best ... khay

---

