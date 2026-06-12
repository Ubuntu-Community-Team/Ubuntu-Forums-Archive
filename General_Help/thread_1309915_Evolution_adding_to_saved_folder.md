---
title: "Evolution adding to saved folder ?"
date: 2009-11-01
forum: General Help
---

### Post by dvsapp on 2009-11-01
I trying to do something, maybe all wrong, but we'll see.;)  I set up Evolution to use a network drive for it's working folder so I can access my e-mail on multiple machines. I got it to work (sort of) and I can get e-mails and view them on each machine. The problem is, if I move something to the "saved" folder, it may or may not return an error regarding saving the file. If I close and reopen Evolution, I now have multiple copies of every e-mail in the folder. It seem that it is appending to the file upon each save rather than overwriting it, (example 2>4>8>16>32> etc). I have no idea if their is a setting for this or what to try. I'd like to stick with Evolution because it will do e-mail and act as a PIM as well.

Any advice welcome.

---

### Post by dvsapp on 2009-11-02
Update:

It seems Evolution will save folders OK if they are unchanged. If any messages are moved to another folder or deleted the file/folder starts screwing up. To move my data folder what I did was to make my network folder, say /home/networkdata/.evolution. I then  opened terminal and typed "ln -s /home/networkdata/.evolution /home/user" Yet, if I put my backup in the original /home/user/.evolution folder, then everything works again.

---

### Post by dvsapp on 2009-11-03
Update 2

I tried creating a symbolic link to a folder on my desktop and Evolution works fine. The problem only happens when I link to a network folder. I want to do something with Gnu cash as well, but I certainly don't want that working file screwed up!  I've tried searching the forums for something where someone has been successful in sharing Evolution in a networked environment, but found little info. I feel like I'm the only one who's trying this. Is it worth reporting as a bug?

---

### Post by dvsapp on 2009-11-03
I found the issue is not just with Evolution because Thunderbird doing strange things as well. I will resubmit the question.

---

### Post by dcstar on 2009-11-03
> **dvsapp said:**
> I trying to do something, maybe all wrong, but we'll see.;)  I set up Evolution to use a network drive for it's working folder so I can access my e-mail on multiple machines.
.........

Any advice welcome.

Any folder for a Linux program **must** have full Linux filesystem support.

If the network resource does not provide this, then it will not work correctly.

---

### Post by dvsapp on 2009-11-03
Thanks for the reply. ALL machines are running Jaunty. The only difference is the "file host" is running an Ext-4 file system while the clients are EXT-3. Could it be that simple?

---

