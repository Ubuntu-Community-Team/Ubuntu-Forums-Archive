---
title: "Cannot Install Updates"
date: 2012-03-06
forum: General Help
---

### Post by mikegior on 2012-03-06
Hello all,

I want to say this issue started sometime last week when the only available update was: Ubuntu One CouchDB (0.3.0-0ubuntu2.1) when I tried to apply this available update, I received the following error:

```

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'google-musicmanager-beta' is missing final newline
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

```

Today, there are more available updates. Thinking last week was a fluke, I tried updating again and got the error above as well. Since it appears Google Music Manager is creating an issue preventing updates from installing (also granted I don't even use it anymore) I decided to uninstall it.

To uninstall it, I tried opening a terminal and doing 'sudo apt-get remove google-musicmanager' When apt-get beings to get everything ready to uninstall it, I get this error message:

```

dpkg: unrecoverable fatal error, aborting:
 files list file for package 'google-musicmanager-beta' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

This is a nuisance. I want to update my system to ensure security. Does anyone have any ideas?

---

### Post by Diametric on 2012-03-06
If you want to force the removal of the package, you can try this:

```
dpkg --remove --force-remove {packagename}
```

---

### Post by cortman on 2012-03-06
Run

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

And see if you get the same error.

---

### Post by mikegior on 2012-03-06
Hey guys,

Thanks for your help. Unfortunately, these methods didn't work for me :( and I'm still stuck.

I looked in /usr/bin and the binary 'google-musicmanager' exists, but the file the apt-get keeps looking for and failing on is 'google-musicmanager-beta' which I can't find on my system. The update utility even attempted a partial upgrade but failed on every package. 

This Google Music Manager is really screwing up everything. Any other ideas?

---

### Post by raja.genupula on 2012-03-06
man we shouldn't go for this > The update utility even attempted a partial upgrade but failed on every package.  it will takes your system to unstable mode . 
[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by Script Warlock on 2012-03-06
> **mikegior said:**
> Hey guys,

Thanks for your help. Unfortunately, these methods didn't work for me :( and I'm still stuck.

I looked in /usr/bin and the binary 'google-musicmanager' exists, but the file the apt-get keeps looking for and failing on is 'google-musicmanager-beta' which I can't find on my system. The update utility even attempted a partial upgrade but failed on every package. 

This Google Music Manager is really screwing up everything. Any other ideas? still no luck with sudo dpkg --configure -a?

---

### Post by mikegior on 2012-03-06
> **Script Warlock said:**
> still no luck with sudo dpkg --configure -a?

Nope :(

---

### Post by Script Warlock on 2012-03-06
can you remove the google music manager with this command? 
> sudo apt-get purge google-musicmanager-beta

---

### Post by sikander3786 on 2012-03-06
Hi!

You are stuck in a similar problem as this one:

[http://ubuntuforums.org/showthread.php?t=1154174](http://ubuntuforums.org/showthread.php?t=1154174)

And the solution lies in post # 4:

[http://ubuntuforums.org/showpost.php?p=7250398&postcount=4](http://ubuntuforums.org/showpost.php?p=7250398&postcount=4)

However, as 'google-musicmanager-beta' isn't available in the official repositories, at the re-install step, you might need to install the package manually. For instance:

```
cd ~/Downloads # get to the directory which contains your downloaded package
sudo dpkg -i <package name>
```

And continue with the other steps in that post.

---

### Post by Bobhuber on 2012-03-06
This might also help.
[http://ubuntuforums.org/showthread.php?p=11743822#post11743822](http://ubuntuforums.org/showthread.php?p=11743822#post11743822)

---

