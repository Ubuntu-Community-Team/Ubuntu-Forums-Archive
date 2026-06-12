---
title: "Not able to uninstall Dictionary"
date: 2010-10-01
forum: General Help
---

### Post by john77eipe on 2010-10-01
I would like to uninstall  the default Dictionary that comes with Ubuntu. (It's under Applications>Office). But I'm not able to find it in SoftwareCenter or in Package manager.

---

### Post by gandaran on 2010-10-01
the dictionary is part of gnome-utils package, to remove this package you have to remove the whole ubuntu desktop!

---

### Post by john77eipe on 2010-10-01
Ok... why i wanted to uninstall is because i get this error when using it
" Error while retrieving the definition
Lookup failed for host 'dict.org': Unknown error "

---

### Post by andrewthomas on 2010-10-01
try to 

```
sudo aptitude reinstall gnome-utils
```

---

### Post by wojox on 2010-10-01
> **john77eipe said:**
> Ok... why i wanted to uninstall is because i get this error when using it
" Error while retrieving the definition
Lookup failed for host 'dict.org': Unknown error "

You are connected to the Internet? Can you access that from a web browser?

```
http://www.dict.org
```

---

### Post by john77eipe on 2010-10-02
it doesn't help.... anyways leave it. It's not a big issue. I could add it to my long list of apps that are installed but don't work!!!

---

### Post by GiveLove on 2010-10-14
Hello People, :)

I just recently am having this same problem of gnome-dictionary not working where it previously worked with no problem. Word look ups end up with the following error message:

> Error while looking up definition

Connection timeout for the dictionary server at 'dict.org:2628'

And the web site, [http://www.dict.org/](http://www.dict.org/)  does not resolve or load within Firefox. This seems to imply it's the web site that is at fault. I did a domain name lookup with Ubuntu's Network Tools, and it gave me 67.215.65.132. I was also unable to bring up the web site with this direct IP address.

In the mean time I'm going to install Artha. But it would be nice if we could figure out what is going on here. Thanks

GiveLove

---

### Post by trukker on 2010-10-16
Same problem here... dictionary not working on upgrade from 10.04 to 10.10

Any ideas?

---

### Post by claracc on 2010-10-16
Same problem since I upgraded to lucid lynx one week ago (with karmic koala, gnome dictionary worked like a charm).

Now when I look for a word, I always obtain the same answer: Connection to dictionary server has failed in dict.org:2628.

If I try to connect via browser (epiphany or firefox) with [http://www.dict.org/](http://www.dict.org/), I obtain: Forbidden

You don't have permission to access /bin/Dict on this server.

What's the matter?, Has it changed the IP address of dictionary server?.

---

### Post by john77eipe on 2010-10-16
Solution:
Abandon the usage of default dictionary until someone finds a fix.
Install Artha. It's pretty good.

---

### Post by claracc on 2010-10-16
> Solution:
Abandon the usage of default dictionary until someone finds a fix.
Install Artha. It's pretty good.

Thanks, yes I have installed artha an it is a very good dictionary.

---

### Post by darryls on 2010-10-16
> **claracc said:**
> Same problem since I upgraded to lucid lynx one week ago (with karmic koala, gnome dictionary worked like a charm).

Now when I look for a word, I always obtain the same answer: Connection to dictionary server has failed in dict.org:2628.

If I try to connect via browser (epiphany or firefox) with [http://www.dict.org/](http://www.dict.org/), I obtain: Forbidden

You don't have permission to access /bin/Dict on this server.

What's the matter?, Has it changed the IP address of dictionary server?.
I'm using lucid (10.04) and experiencing identical solutions.  Using:
> 
lynx -head -dump [http://www.dict.org](http://www.dict.org)

... indicates the server is up but is experiencing some form of problem.

---

### Post by john77eipe on 2010-10-18
darryls@ Lynx? I havn't used it before. Seems to be like a micro browser or something!! :p

---

### Post by lisati on 2010-10-18
> **john77eipe said:**
> darryls@ Lynx? I havn't used it before. Seems to be like a micro browser or something!! :p

It's a [browser]("http://en.wikipedia.org/wiki/Lynx_%28web_browser%29"). Until I started using these forums, I thought Lynx was a deodorant or a member of the cat family. :D

---

### Post by john77eipe on 2010-10-18
:lolflag: That was comforting.

---

### Post by walshy2 on 2010-10-18
I am having the same problem any luck yet:confused:

---

### Post by john77eipe on 2010-10-18
Nope. Try Artha.

---

### Post by john77eipe on 2010-10-18
[www.dict.org](www.dict.org) opens fine in my browser. Seems they have changed their ip. And I think in dictionary source code they might have coded in the ip address.

If anyone knows how to modify it. Please reply. 



PS: I'm a newbie!!

---

### Post by GiveLove on 2010-10-19
Hey People, :)

[www.dict.org](www.dict.org) also opens fine in my browser now. And gnome-dictionary is working normally again. 

john77eipe,

I still get the same IP address from a lookup as I did in my prior post. But I noticed I get different results if the "http://" is not part of the lookup. I don't know why that would make a difference. So if the IP address is still the same, then I would guess that they must have been having server issues or hardware upgrades on their end to have caused an entire service outage.

---

### Post by john77eipe on 2010-10-20
gnome-dictionary still not working for me!

---

### Post by claracc on 2010-10-20
It works now.

Perhaps you have to set in edit --> preferences -->font, predetermined dictionary server.

---

### Post by GiveLove on 2010-10-21
After a brief one day period of the gnome-dictionary working again, it's back to no longer working. And the [www.dict.org](www.dict.org) web site not loading. I guess I spoke too soon? LOL

---

### Post by ThePhysician on 2010-10-21
I am also having this problem.

Add it to the mile long list of bugs in Ubuntu.

---

### Post by PJSingh5000 on 2010-10-21
> **ThePhysician said:**
> Add it to the mile long list of bugs in Ubuntu.

We'll also have to add it to 100 mile long list of bugs in Windows, because I can not open [http://www.dict.org](http://www.dict.org) in IE8 on my XP laptop!

---

### Post by john77eipe on 2010-10-24
It has already been reported. Since it's not exactly a ubuntu problem. The request is for adding alternative servers.
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/660259](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/660259)

---

### Post by oldwismn on 2010-10-25
The page here [http://choorucode.wordpress.com/2010/04/10/ubuntu-offline-gnome-dictionary/](http://choorucode.wordpress.com/2010/04/10/ubuntu-offline-gnome-dictionary/) tells how to install a local dictionary as a new dictionary source.  Now my Dictionary application is working again and as an added benefit, I can use it offline.

---

### Post by colin.p on 2010-10-25
> **oldwismn said:**
> The page here [http://choorucode.wordpress.com/2010/04/10/ubuntu-offline-gnome-dictionary/](http://choorucode.wordpress.com/2010/04/10/ubuntu-offline-gnome-dictionary/) tells how to install a local dictionary as a new dictionary source.  Now my Dictionary application is working again and as an added benefit, I can use it offline.

Works a treat, thanks

---

### Post by john77eipe on 2010-10-26
oldwismn,

How do i use it without installing the server? What would be the IP address?

---

### Post by oldwismn on 2010-11-02
To use the local dictionary, install the dictd package, which includes the server and client, and the English dictionary, dict-gcide.  Use the loop back IP address, 127.0.0.1.

By the way, the online default dictionary server is working now.

---

