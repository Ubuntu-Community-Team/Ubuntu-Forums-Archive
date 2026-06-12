---
title: "Using sudo to change file ownership"
date: 2009-09-09
forum: General Help
---

### Post by HANGBELLY on 2009-09-09
I recently tried to add some add-ons to the script file in Gimp, but I got an error message saying that I did not have read/write permission for that file. When I right clicked and chose properties and clicked the permissions tab, I was told that I was not the owner of the file (even though mine is the only  user on the system), and I needed to be in root. 
  Rather than activating a root account, is it possible to change the ownership of the file in sudo? Or is there another way. Also, why would I not be considered the  owner of a file if I'm the one who downloads it?
                                                              Thanks for the help.

---

### Post by shae on 2009-09-09
The best place to put plugins you add to gimp is in your ~/.gimp-2.6 folder.  There should be a subfolder called plugins or scripts, but I cannot check right now as I do not have access to a Linux computer at the moment.

---

### Post by HANGBELLY on 2009-09-09
> The best place to put plugins you add to gimp is in your ~/.gimp-2.6 folder. There should be a subfolder called plugins or scripts, but I cannot check right now as I do not have access to a Linux computer at the moment.


That's where I'm trying to put them, but for some reason I only have read permission, not write. When I try to change this, it tells me I need to be in root to write to that file. I want to change the ownership of the file so I don't have this problem anymore. But at the same time, I don't want to activate a root account for safety reasons.

---

### Post by NoaHall on 2009-09-09
"chmod rw" or "sudo chmod rw"

---

### Post by shae on 2009-09-09
Hmm what are the permissions of the file?  Are they in fact root only because they should be owned by you unless you used root to copy or started gimp as root.

You should try
```
sudo chown *yourusername*:*yourusername* *filename*
```

---

### Post by HANGBELLY on 2009-09-10
> Hmm what are the permissions of the file? Are they in fact root only because they should be owned by you unless you used root to copy or started gimp as root.

You should try
     Code:
     sudo chown *yourusername*:*yourusername* *filename*
That's what I did and it worked. I got confused because the scripts file in Gimp is listed as owned by root, and users don't have permission to make changes. Since the root account is not turned on by default in Ubuntu, I thought I would have to turn on the root account to make the changes. I didn't think it would be as easy as entering sudo. Consider this problem solved.
                                                                          Thanks for the help.

---

### Post by snakeman21 on 2009-09-10
You shouldn't have to change ownership.  You should be able to open a Terminal and type:

```
gksudo gedit path/to/file/filename
```

That will open it with root permissions, and you should be free to edit it to your heart's content.

---

### Post by HANGBELLY on 2009-09-10
Cool, that's what I like about this forum. You learn different ways of doing things. I first learned how to set up Ubuntu from a couple of books, but now maybe I can move up from being a dumb user.:)
                                                                                  Thanks again.

---

### Post by snakeman21 on 2009-09-10
No problem!  Posting here is like my way of "giving back."  These forums saved my @$$ many times when I was starting out.  Soon, you'll be doing the same thing.

---

