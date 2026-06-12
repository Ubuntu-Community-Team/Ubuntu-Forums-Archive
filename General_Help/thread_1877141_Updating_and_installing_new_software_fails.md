---
title: "Updating and installing new software fails"
date: 2011-11-07
forum: General Help
---

### Post by jonnywombat on 2011-11-07
Hi there all,

Having a little problem updating and installing software via software centre.

Basically I cannot do either, and I have not had a successful update for about 2 weeks. I cannot identify reason for this to have happened.

If I try 
```
sudo apt-get update
``` 

then I get the following output


```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://gb.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```


any ideas how to correct this??

Many thanks

Jonny

---

### Post by BillyBoa on 2011-11-07
Go to Software Sources and on the tab Ubuntu Software go down to Download from and choose other and then select best server. Wait and select the best server.

---

### Post by jonnywombat on 2011-11-07
Hi there, 

Thanks for the reply, 

I have done that a few times, makes no difference if I use main server or the UK (my local) server

Jonny

---

### Post by BillyBoa on 2011-11-07
Then you need to do this:
[http://www.howtogeek.com/72934/how-to-automatically-import-missing-gpg-keys-in-ubuntu/](http://www.howtogeek.com/72934/how-to-automatically-import-missing-gpg-keys-in-ubuntu/)

---

### Post by Enigmapond on 2011-11-07
This seems to be a GPG key problem. Try running these commands in terminal:

```
$ sudo -i

# apt-get clean

# cd /var/lib/apt

# mv lists lists.old

# mkdir -p lists/partial

# apt-get clean

# apt-get update
```

Then 

```
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update && sudo apt-get update
```

This comes from this source:
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by jonnywombat on 2011-11-07
Hi Again

Thanks for the link, I installed that tool but still get the same error after running it.

Jonny

---

### Post by jonnywombat on 2011-11-07
Hi enigmapond, 

Thanks for that, I can now use software centre again, and update manager is not throwing an error, but not offered an update either.

Jonny

---

### Post by Enigmapond on 2011-11-07
No problem.:D Somewhere along the line the directory got fouled. So run an update in the terminal and post the output here between the CODE tags. You should have gotten an update is it's been 2 weeks.

---

