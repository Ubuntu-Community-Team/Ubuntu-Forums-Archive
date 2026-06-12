---
title: "Firefox error Ubuntu 11.04"
date: 2011-08-06
forum: General Help
---

### Post by flash100890 on 2011-08-06
Ubuntu shows the following error message when I try to launch Firefox

              "Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

                  No other program including Google Chrome has this problem.:confused:

---

### Post by ~!geek!~ on 2011-08-06
I hope you have checked the space available in your home directory and am assuming there is sufficient space available there.

You may try to investigate the ~/.mozilla directory of your machine. This is the directory which holds all settings of mozilla products: firefox, thunderbird ..... 
(Before running any of the commands in the post, firefox should not be running. If you are running firefox to read this, just copy the text and terminate the firefox program)
As its not the disk space problem, it may be associated with permissions of files in the mentioned directory. 
For this, you may try this commands:
> sudo chown <yourusername> ~/.mozilla -R 
This will make you the owner of all files and directories of .mozilla directory.
Then try 
>  sudo chmod 700 ~/.mozilla -R 
It will give you and only you, all rights on this directories recursively.
Now you may start firefox and check if its solved.

If above steps don't help you, in worst case you may have to remove (don't delete but cut and paste the directory somewhere say desktop as a backup), the directory containing profile you use for firefox contained in ~/.mozilla/firefox directory. For doing this you may use: 
> mv ~/.mozilla/firefox ~/Desktop/firefoxbackup 
Now start the firefox.
By now, I hope you might  have got your problem solved.

---

### Post by flash100890 on 2011-08-07
My home directory does have enough space, and I'm afraid that none of the above suggestions solved my problems but thanks for your help.

---

