---
title: "Recursive directory structure"
date: 2009-08-06
forum: General Help
---

### Post by max-power2717 on 2009-08-06
Hi Community :).

Have used Ubuntu successfully and often for over a year now, without much trouble. I've been very happy with it (I'm using 8.04).

I wanted to clean my hard drive and install 9.04, so I decided I'll just copy my Home directory to a windows machine on my home network. Unfortunately I ran into the trouble of a recursive string of directories (I believe they're called symbolic links). it started with .gvfs directory and it goes: [INDENT].gvfs/windows_machine_share/my_home_folder/.gvfs/windows_machine share/... 
[/INDENT]What should have been a 2 Gb transfer, I canceled after 5Gb.

I've tried deleting the folder that's now on my windows machine from both windows explorer and nautilus in ubuntu, neither succeeded. 

I found a thread from a while back about using the console to remove the original link, but that was on the Ubuntu partition. I don't know how to manipulate the files on my windows machine with the console from Ubuntu to try to fix this problem. 

Can anyone tell me how to access a windows share from the console (as if it were on the local machine). 

Is there a better way this problem should be fixed (maybe the best way is to find a solution on the windows machine? I wouldn't expect wondows support here, but please anyone, let me know if you think it's no good trying to fix the problem from Ubuntu)

Thanks in advance for any advice.

---

### Post by giggins on 2009-08-06
Is "my_home_folder" a symlink? You can tell by going to a terminal and typing this:

```
cd ~/.gvfs/windows_machine_share/
ls -alh my_home_folder
```

If that's the symlink, then you can safely remove it with this command:

```
rm my_home_folder
```

I think you will have better success copying your home directory to somewhere local **before** mounting your windows share, since gnome's gvfs will mount your windows share within your home directory. If you have the space, copy it to /tmp or you could do this:

```
cd /home
sudo tar zcvf myhome.tgz <username>
sudo chown <username>:users myhome.tgz

```

Obviously, replace <username> with your username.

Then mount your windows share and copy the .tgz file, which now contains all your data in a compressed tarball.

---

### Post by max-power2717 on 2009-08-07
Hi, cheers for the tips.

I did what you suggested to find out which file was the link: 

[LIST]
[*]started up my Ubuntu machine
[*]mounted the windows share with the infinitely recursing directory structure ("windows_machine_share")
[*]pointed the console to ~/.gvfs/windows_machine_share (My understanding is that this the console is now operating on the directory shared from windows)
[*]ls -alh my_home_folder
[/LIST]
This showed no links, everything shows up as a directory.

I also checked other directories for links from Ubuntu, but I found none (I only checked 3 levels of recursion, but everything shows up as a directory).

Maybe I was wrong about the symbolic link, or perhaps when I attempted the copy to windows which went wrong, the symbolic link was stored on the windows NTFS partition as a directory. Can anyone enlighten me?

Despite not finding a symbolic link, I tried to remove the recursing directory structure stored on the windows machine from ubuntu with 
```
cd ~/.gvfs/windows_machine_share
rmdir my_home_folder
```This fails: rmdir reports "failed to remove 'my_home_folder': Device or resource busy". I don't know what that means exactly

So, I still have this directory in my windows machine that I can't get rid of. Any suggestion anyone? Any help will be heaps appreciated.

Thanks giggens for the tip about archiving the home directory before transferring. Just did it now, and no worries. Can safely do the format and reinstall. 

Now if I could just find a way to remove the infinitely recursing file structure on my windows machine. 

Cheers,
Max.

---

### Post by giggins on 2009-08-07
Try running this:

```
mount
```

Check if anything is mounted at 'my_home_folder'. If it is, you can unmount it first, using 'umount <directory>'. Maybe you already have a shell open, or a file browser open in that directory, or one of its subdirectories, so you can't delete it. I don't usually use the 'rmdir' command, I just use 'rm -rf' when I'm sure I'm deleting a directory I know I don't need.

You are correct that Windows filesystems (both NTFS and FAT) do not support symlinks. You likely had a symlink within your home directory, and that was converted to a directory containing the linked-to directory. Pretty ugly stuff, I know.

---

