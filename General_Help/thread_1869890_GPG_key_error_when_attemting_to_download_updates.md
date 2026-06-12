---
title: "GPG key error when attemting to download updates"
date: 2011-10-26
forum: General Help
---

### Post by airplanesimen on 2011-10-26
```
 W: GPG error: http://no.archive.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://no.archive.ubuntu.com oneiric-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://no.archive.ubuntu.com oneiric-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://extras.ubuntu.com oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```i got this pubkey error when i try to download and install updates. when i tried in the update manager, it said it required something... untrusted packages.

Help?

---

### Post by ubupirate on 2011-10-26
[http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

That should fix it right up.

---

### Post by drs305 on 2011-10-26
If you just want to add the one repository key generating the errors:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 3E5C1192
sudo apt-get update
```

---

### Post by airplanesimen on 2011-10-26
> **drs305 said:**
> If you just want to add the one repository key generating the errors:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 3E5C1192
sudo apt-get update
```
still getting this:

```
Reading package lists... Done
W: GPG error: http://no.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://no.archive.ubuntu.com oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://no.archive.ubuntu.com oneiric-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by drs305 on 2011-10-26
Try opening Software Sources, go to the Authentication tab, and remove the keys for Extras and Ubuntu Archive. If you also see one for Security, remove that one as well.

Then run 'sudo apt-get update' again. You will get the authentication errors. Copy the numbers to the following command (you can use the full code rather than just the last 8 characters) and try adding them again.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys < *add keys here* >  
```

I changed to the Norway server and the keys imported correctly for me, but if the above fails you might try changing servers from the Ubuntu Software tab.

---

### Post by airplanesimen on 2011-10-26
> **drs305 said:**
> Try opening Software Sources, go to the Authentication tab, and remove the keys for Extras and Ubuntu Archive. If you also see one for Security, remove that one as well.

Then run 'sudo apt-get update' again. You will get the authentication errors. Copy the numbers to the following command (you can use the full code rather than just the last 8 characters) and try adding them again.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys < *add keys here* >  
```

I changed to the Norway server and the keys imported correctly for me, but if the above fails you might try changing servers from the Ubuntu Software tab.
 It worked :D Thankyou for your help guys :P

---

### Post by airplanesimen on 2011-10-26
can someone just give me a step for step description?

Got the same problem again...:(

---

### Post by airplanesimen on 2011-10-26
> **drs305 said:**
> Try opening Software Sources, go to the Authentication tab, and remove the keys for Extras and Ubuntu Archive. If you also see one for Security, remove that one as well.

Then run 'sudo apt-get update' again. You will get the authentication errors. Copy the numbers to the following command (you can use the full code rather than just the last 8 characters) and try adding them again.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys < *add keys here* >  
```I changed to the Norway server and the keys imported correctly for me, but if the above fails you might try changing servers from the Ubuntu Software tab.
thhe place where i should add the key, should i only add this: ```
 BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key 
```
or only this: 
```
 16126D3A3E5C1192
```?

---

### Post by drs305 on 2011-10-26
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

When you accomplished the earlier steps, did you also remove the key for Extras in the Authentication tab of Software Sources before running the above command? How you get to Software Sources depends on which release of Ubuntu you are using. If you don't know how to open it, just ask.

---

### Post by airplanesimen on 2011-10-26
> **drs305 said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```When you accomplished the earlier steps, did you also remove the key for Extras in the Authentication tab of Software Sources before running the above command? How you get to Software Sources depends on which release of Ubuntu you are using. If you don't know how to open it, just ask.
yes went in there and removed them. after upgrading, these problems has occured to me. and it doesnt seemes to help at all, the same error comes every time,..

---

### Post by dhaneshr on 2011-10-26
This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

dhaneshr

---

### Post by drs305 on 2011-10-26
You will have to clean out your cache and the old lists.  To do this...

Edit: Nevermind. Thanks *dhaneshr*

---

### Post by airplanesimen on 2011-10-27
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

dhaneshr

Sorry, didnt help... Exact same error again...

---

### Post by airplanesimen on 2011-10-28
thanks to drs305 for the help ^^ it worked :P Thank you all for your help ;)

---

### Post by airplanesimen on 2011-10-28
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

dhaneshr
SOLVED with this, thanks!:popcorn: After doing these commands, i added the keys with the command above. i restarted, and whoopie!

---

### Post by saphil on 2011-11-13
When I try this code the output is that it doesn't find any trusted key.

```

wolf@telcontar2:~/Downloads$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.UNU3iyIDKz --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
wolf@telcontar2:~/Downloads$ 


```

---

### Post by saphil on 2011-11-13
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```dhaneshr

That piece cleared the error messages, Thanks!

---

### Post by newb85 on 2011-11-15
When the above didn't resolve the issue for me, I took to following steps recommended by another forum:

> cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

That took care of it.  It would be a little more educational, though, if I understood what I just did.  The file manipulation commands are easy enough, but what exactly is the purpose of the directory /var/lib/apt/lists?  Did the above procedure essentially amount to clearing some sort of cache?

Thanks!

---

### Post by drs305 on 2011-11-15
> **newb85 said:**
> When the above didn't resolve the issue for me, I took to following steps recommended by another forum:



That took care of it.  It would be a little more educational, though, if I understood what I just did.  The file manipulation commands are easy enough, but what exactly is the purpose of the directory /var/lib/apt/lists?  Did the above procedure essentially amount to clearing some sort of cache?

Thanks!

If you look at the /var/apt/lists folder you will see a large number of files. These files contain information about the various packages available in the repositories. The 'partial' subfolder contains additional information that is, as one site describes it, 'transitory' in nature.

Something in one of these folders became corrupted, and moving all the files/folders to a new location forces APT to recreate them with fresh and hopefully uncorrupted information. 

So to answer your question, yes, it is similar to clearing a cache.

---

### Post by Jacobonbuntu on 2011-11-15
> **ubupirate said:**
> [http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

That should fix it right up.


thanks! worked for me too :)

---

### Post by beenny on 2011-11-27
thanks worked for me also...

---

### Post by 14quartz on 2011-12-04
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```dhaneshr


This really solved my problem.... Thanks a lot buddy.....
Now update is happening without any issue.

---

### Post by morgenroete on 2012-05-25
yes, it also works for me in Ubuntu 12.04. :popcorn:

---

### Post by psyclops on 2012-08-25
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```dhaneshr

Thanks man, this worked like a charm :grin:

---

### Post by mungatsuma on 2012-10-04
> **psyclops said:**
> Thanks man, this worked like a charm :grin:

Tried it but still get errors.
> W: GPG error: [http://download.opensuse.org](http://download.opensuse.org) ./ Release: The following signatures were invalid: KEYEXPIRED 1307152882
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2693D732CA213C67
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) lucid-ladish Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2693D732CA213C67

Though the errors reduced some, but these wont go.

---

### Post by airplanesimen on 2012-10-04
Do this:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2693D732CA213C67
```

then:
```

sudo apt-get update
```

Post here if it didn't work.

---

### Post by mungatsuma on 2012-10-12
The errors remained, decided to do a fresh install of vanilla ubuntu and customise for design. Now having issues with kxstudio archives

Getting these errors;
> W: GPG error: [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D3445A829213837
W: Failed to fetch [http://kxstudio.sourceforge.net/repo/dists/precise/free/source/Sources](http://kxstudio.sourceforge.net/repo/dists/precise/free/source/Sources)  404  Not Found

W: Failed to fetch [http://kxstudio.sourceforge.net/repo/dists/precise/non-free/source/Sources](http://kxstudio.sourceforge.net/repo/dists/precise/non-free/source/Sources)  404  Not Found


Have already tried the solutions given in above posts , but no luck.

---

### Post by metos on 2012-11-09
> **dhaneshr said:**
> This should solve your problem:

```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```dhaneshr

woked fine for me on my 12.04 :)
thanks

---

