---
title: "Can't play many flash videos in firefox"
date: 2009-06-26
forum: General Help
---

### Post by derkrampus on 2009-06-26
I'm having trouble with a lot of Flash videos in Firefox on Ubuntu.  They play file in Firefox on Windows.  My main concern is getting the website pornhub working on ubuntu?  Can someone point me in the right direction as to why the movies don't play?  Does the website work for other users on ubuntu firefox?  

Note that the videos show fine on the home page, but do not play when you try to view the actual video.

Hope you understand my concern. 

Thanks! J

---

### Post by flugh on 2009-06-26
I recently fixed my freezing on flash problems by removing all of the swfdec packages. A lot of Googles turned up this fix in several different places, and it worked for me. YMMV.

Can't speak for that specific site however. I consume zero pr0n (unless you count some of the /dancing my mule does while scanning Auction House in Stormwind).

---

### Post by philcamlin on 2009-06-26
hehe porn :D :popcorn:

reinstall flash?

---

### Post by synapsys on 2009-06-26
I am wondering.... did you ever install flash in the first place?

open up a terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by raymondh on 2009-06-26
ubuntu-restricted-extras

---

### Post by Therion on 2009-06-26
Install the Adobe flash plugin.

Open Synpatic and search on **swfdec**.  You should get two hits on this search.  Mark them both for removal if installed.

Now, while still in Synpatic, search on **gnash**.  Uninstall any packages you find.

This should solve the problem.

---

### Post by Vicedi on 2009-06-26
What Therion said to do WORKS!

---

### Post by lovinglinux on 2009-06-26
> **Vicedi said:**
> What Therion said to do WORKS!

Just for future reference...

This solution is also in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by derkrampus on 2009-07-26
Installing these packages didn't fix the problem.

sudo apt-get install flashplugin-nonfree
sudo apt-get install ubuntu-restricted-extras

So I went to synaptic and removed the swfdecpackages.  This completed the universe and the people rejoiced.  Thanks everyone!!!

I work for a windows shop and am not well versed in linux :(

---

