---
title: "Aptitude/Dpkg error"
date: 2010-02-28
forum: General Help
---

### Post by waveslider on 2010-02-28
I was happily following an intrusion-detection tutorial from the Security category this morning and was nearly finished with installing Snort from the repos with aptitude (it was running the post-installation configuration script), when KDE crashed on me.

After restarting, I get errors from aptitude when I try to complete the installation. I first tried ```
sudo dpkg --configure -a
``` as aptitude suggested then ```
sudo aptitude reinstall snort
``` then I tried ```
sudo aptitude remove snort
``` then I tried ```
sudo aptitude install snort
``` again, with no success. Finally, I tried ```
sudo aptitude purge snort
``` and ```
sudo aptitude install snort
``` but it did not work.

Now no matter what I do with aptitude, I get the following error message from dpkg:

```

dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing snort (--configure): subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing: snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I have reached the extent of my aptitude knowledge here. Can anyone please tell me how to repair it?

Thanks!

---

### Post by Zorael on 2010-02-28
Find the .deb in **/var/cache/apt/archives/** and try to install it manually with dpkg -i.
```
$ ls /var/cache/apt/archives/snort*
$ sudo dpkg -i /var/cache/apt/archives/snort_*<version>*.deb
```
Now you should get a more verbose error message. See what it complains about.

If it's a duplicate file you can force it with **--force-overwrite**.

---

### Post by waveslider on 2010-02-28
Cool, thank you very much.

I tried that, and this is the output I received:

```

Preparing to replace snort 2.8.4.1-3ubuntu1 (using .../snort_2.8.4.1-3ubuntu1_amd64.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error              
dpkg: warning: old pre-removal script returned error exit status 2                          
dpkg - trying script from the new package instead ...                                       
dpkg: ... it looks like that went OK.                                                       
usermod: no changes                                                                         
Unpacking replacement snort ...                                                             
dpkg (subprocess): unable to execute old post-removal script: Exec format error             
dpkg: warning: old post-removal script returned error exit status 2                         
dpkg - trying script from the new package instead ...                                       
dpkg: ... it looks like that went OK.                                                       
Setting up snort (2.8.4.1-3ubuntu1) ...                                                     
update-rc.d: warning: /etc/init.d/snort missing LSB information                             
update-rc.d: see <http://wiki.debian.org/LSBInitScripts> 

```

When I tried it with the --force-overwrite option, it simply print this:

```
                                                    
Setting up snort (2.8.4.1-3ubuntu1) ...                                                     
update-rc.d: warning: /etc/init.d/snort missing LSB information                             
update-rc.d: see <http://wiki.debian.org/LSBInitScripts> 

```

I read the wiki entry for LSB init scripts, but that stuff is also on a higher knowledge level than I currently have. 

Any suggestions? And again, thanks for your help!

---

