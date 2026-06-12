---
title: "Failed to fetch"
date: 2010-05-24
forum: General Help
---

### Post by Jae99 on 2010-05-24
Hey I have quick question. I am trying out backtrack 4 final (based on Ubuntu) and I tried to update it with the apt-get update command and I always receive:

Failed to fetch [http://archive.offensive-security.com/pool/universe/libt/libtar/libtar_1.2.11-5_i386.deb](http://archive.offensive-security.com/pool/universe/libt/libtar/libtar_1.2.11-5_i386.deb)  Could not resolve 'archive.offensive-security.com'

I know its not my internet connection because I made this post on the same connection. Thanks in advance for any help.

---

### Post by rob-ward on 2010-05-24
on the commandline can you ping sites for example 
```
ping google.com
```
because while your internet may be fine your commandline could be using another proxy(or more likely no proxy where one is needed)

ALso it might we worthwhile trying to do a 
```
wget http://archive.offensive-security.com/pool/universe/libt/libtar/libtar_1.2.11-5_i386.deb 
```

and check that you can download it that way.

I can however confirm the address is ok as my computer just downloaded it when I clicked on your link.

Interestingly however my computer says that I already have a newer version of that package installed on my machine running 10.04, do you know what release backtrack is based on??

if needs be you should be able to find the deb somewhere else or download that version manually through your browser and install it manually so that your update doesn't try to get it, however that won't fix the issue of it not resolving archive.offensive-security.com if there are lots of updates needed.

---

### Post by Jae99 on 2010-05-25
You are correct rob-ward that everything else is connected to the net except my command line. I just never though of that. Does anyone gave any idea how to fix this? Thanks again rob-ward.

---

### Post by rob-ward on 2010-05-25
My guess is that you have a proxy set in your web browser that you don't have for Backtrack as a whole.

I assume you are using firefox, if you are to find proxy information it is in Edit -> preferences -> Advanced -> Network  -> Settings

Is there a proxy set in there???

If there is then the details that are in there probably need putting into the system proxy, in Ubuntu that is under System -> Preferences -> Network Proxy  I assume it is the same or similar in Backtrack


If there isn't a proxy set in firefox then if you look in the System -> Preferences -> Network Proxy there might be one set in there that you want to remove. Basically you need to make the system do what firefox is doing as it seems to be working.

Once you have made any changes it is important to keep in mind that you need to click apply system wide for it to take effect(take a screenshot of the details that are currently there if you change anything then you know how to put things back is something goes wrong). It should also be note that you have to close the terminal that is running down and start it again for changes to take effect.

Hope that helps, let us know if that either doesn't work or doesn't make sense etc..

---

### Post by Jae99 on 2010-05-29
I just reformatted by computer and now its works. So I guess i messed up and setting or something. Thanks for the help.

---

