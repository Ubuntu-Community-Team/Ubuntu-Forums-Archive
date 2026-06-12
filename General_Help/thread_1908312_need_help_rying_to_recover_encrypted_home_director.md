---
title: "need help rying to recover encrypted home directory"
date: 2012-01-13
forum: General Help
---

### Post by gargamon on 2012-01-13
Hi,

I lost my root partition but still have my ecrypted /home. I'm trying to decrypt it and recover the data. I have the original passphrase and, of course the encrypted /home directory. 

This was encrypted a long time ago and I recall that I did not use the standard options of aes/16 bit. This prevents me from using the new ecryptfs-recover-private. I used plaintext_passthru and filename_encryption. 

I tried the procedure at [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually) which helped a lot. I can now do the mount and the top level filenames are shown correctly, but I cannot access the files. It says "cannot access XXX: No such file or directory". So I can decrypt the filenames but not the files. 

I tried repeatedly remounting with likely options for cipher and key sizes believing that if I got the right one it would decrypt the files also but had no luck. 

Then I checked syslog and found that there was an error every time I tried to mount: "Error initializing key module [/usr/lib/ecryptfs/libecryptfs_key_mod_gpg.so]; rc = [-22]". Maybe this has something to do with it.

Any and all ideas as to what to try next  would be appreciated.

---

### Post by gargamon on 2012-01-16
Solved. 

I went back and found the instructions I followed to generate the encrypted home dir. When I initially did this there were no easy utilities like there are available now. Then I created a test disk under the same conditions. By piecing together info from that test and parts of the script ecryptfs-recover-private I came up with the solution. After 4 attempts I matched the initial cipher/key length and all was golden.  

I did think it was funny that I had to "ecryptfs-add-passphrase --fnek" before each attempt as the key was no longer available.

---

