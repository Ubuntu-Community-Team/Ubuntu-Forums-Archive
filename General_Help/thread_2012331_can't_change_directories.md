---
title: "can't change directories"
date: 2012-06-28
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-06-28
OK, I have no idea on this one, I sure hope someone can help.

I need to rescue some files on my desktop before reformatting and reinstalling.

I'm running xubuntu on a 4 partition harddrive, xubuntu is the only os on the drive. 

I am running with the live cd, managed to mount the hdd with xubuntu on it and managed to change to the home directory on the harddrive.

When I do an ls command, I can see the folders of the various user folders. So, I should be able to do a simple cd command to get to the desired users folder (in this case, it's 'artie'). But, the output says 'no file or folder'

Here's the output showing the progress so far:


```


ubuntu@ubuntu:/mnt/harddrive/home$ ls
[COLOR=Blue]art  artie  artkits  hannah  temporary[/COLOR]
ubuntu@ubuntu:/mnt/harddrive/home$ cd /artie
bash: cd: /artie: No such file or directory
ubuntu@ubuntu:/mnt/harddrive/home$ cd/ temporary
bash: cd/: No such file or directory
ubuntu@ubuntu:/mnt/harddrive/home$ ls
[COLOR=Blue]art  artie  artkits  hannah  temporary[/COLOR]
ubuntu@ubuntu:/mnt/harddrive/home$ pwd
/mnt/harddrive/home
ubuntu@ubuntu:/mnt/harddrive/home$ cd /hannah
bash: cd: /hannah: No such file or directory
ubuntu@ubuntu:/mnt/harddrive/home$ cd /artie
bash: cd: /artie: No such file or directory
ubuntu@ubuntu:/mnt/harddrive/home$ cd /artkits/
bash: cd: /artkits/: No such file or directory
ubuntu@ubuntu:/mnt/harddrive/home$ ls
[COLOR=Blue]art  artie  artkits  hannah  temporary[/COLOR]
ubuntu@ubuntu:/mnt/harddrive/home$ 



```

I'm sure I've overlooked something, probably something that's very simple.

Any suggestions?

ty

Art

---

### Post by ubudog on 2012-06-29
Try removing the / from in front of the directory name.  For example, running: 
```
cd /hannah
```
will get you into /hannah, not the hannah directory in your current directory.

So, try: 
```
cd hannah/
```

Best of luck!

---

### Post by goodbye-windows(tm) on 2012-06-29
That works, and I never would have thought of that in a million years!! Many tnx.

While I still can't get into the artie folder, I can get into the hannah folder!! Hannah never set a password, which is probably why I can get into her folder without a permission problem (I'm guessing).

When I do a cd artie or a cd artie/, both commands say permission denied. So, it looks like there is a permission problem. 

When I mounted the harddrive, the permissions software probably thinks I'm 'ubuntu', which is the only user on the live cd.

I'll try changing the permissions for that folder to 'ubuntu', and try again.

Again, tnx.

Art

---

