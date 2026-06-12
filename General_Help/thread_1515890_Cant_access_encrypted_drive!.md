---
title: "Cant access encrypted drive!"
date: 2010-06-23
forum: General Help
---

### Post by zelix5 on 2010-06-23
Hi i had fedora 13 on my server system first, and my 2nd hard drive was encryped via fedora.

I can recognize the drive in ubuntu 10 i have on now, and i can type the password in however it says:

> ERROR:
Unable to mount 500GB Encrypted

Error starting job: Failed to execute child process "cryptsetup" (No such file or directory)

Please help!

Thanks

---

### Post by Ric95 on 2010-07-19
I suggest finding out what type of encryption you used with Fedora, and make sure its installed in Ubuntu. 
eg: ccrypt, gpgsm, truecrypt ect...

---

### Post by newbuntuxx on 2010-07-27
Solution:

```
sudo apt-get install cryptsetup
```

---

### Post by aweswald on 2011-03-26
> **newbuntuxx said:**
> Solution:

```
sudo apt-get install cryptsetup
```


That has worked for me! 

You've saved my life!

Thanks!!! Thanks x 10000!

---

### Post by snoopy-2009 on 2011-04-03
hoping this is going to work for me... cryptsetup installing as i type.........

im not sure how i got the error msg 
```
Error starting job: Failed to execute child process "cryptsetup" (No such file or directory)
```to pop up, but once i did, that was the first hint that somthing may not have been installed yet...

ive been locked out of my double encrypted 500gb hdd for about a week, since clean ubuntu install, reading up on different methods (with not much luck) on any possible way to crack it.. i was thinking of using some type of wordlist generator (couldnt find one of those either.. lol) since i knew my password had to at least be CLOSE to what i have written down.. 

ive been completly stumped as to why my passphrase wasnt working..

OMG WOW! this really did work!! im thrilled i got my HDD back!!!!!!! ty so much...well actually, i already had it installing when i loaded this page.. but still, same solution!! 
:lolflag:            :popcorn:            :guitar:

mods: this needs to be marked [SOLVED!] please :)

---

