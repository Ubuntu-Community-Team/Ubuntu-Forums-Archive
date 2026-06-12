---
title: "How can I add symbolic links to /usr/local/bin"
date: 2010-07-10
forum: General Help
---

### Post by Ralph L on 2010-07-10
I am trying to set up scripts to execute Luckybackup and make them easily available to all users of the computer.  Following the recommendation of the web site ([http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)) I tried to set up a folder (/usr/local/myprograms/luckybackup_scripts) containing the scripts, and to put symlinks pointing to the scripts in /usr/lock/bin.  

The object of this design was to have my local programs clearly separate from any other programs, and to point to them with symlinks in /usr/local/bin.  This is because /usr/local/bin is automatically searched when a terminal command is issued so the user need not specify the whole path to the script.

The problem that I ran into was that the system would not let me create symlinks to scripts in /usr/local/myprograms/luchybackup_scripts.  While ths symlink was created, it was invalid and did point to any target.  The only symlinks that I could create had to be in the same folder as the target, namely /usr/local/myprograms/luckybackup_scripts.  I tried to create the links using Terminal and "sudo ln -s ........"

Can anybody explain why I was unable to create the desired symlinks, and whether there is some way I can do so.

Am running Lucid.

Thanks
Ralph

---

### Post by squaregoldfish on 2010-07-10
Can you post the command you were using and the result?
Steve.

---

### Post by Ralph L on 2010-07-10
I tried it several ways, but here was one way.  Note that lbprofile1 is a script contained in /usr/local/myprograms/luckybackup_script.
Commands:
cd /usr/local/myprograms/luckybackup_script
sudo ln -s lbprofile1 ../../bin/lbprofile1

The result was a symlink being created in /usr/local/bin, but it had a bix X through it in Nautilus and no target file listed in Nautilus.

If you need the actual run I will set it up again.  However, it will take some time as I have recreate some things.

Thanks
Ralph

---

### Post by squaregoldfish on 2010-07-10
The problem is that when you create a symbolic link, the system will use the literal text that you give it as the destination, and doesn't take into account where you currently are. So, with the command you gave, you'll have the following in /usr/local/bin:
```

lbprofile1 -> lbprofile1
```without any path.

What you have to do is:
```

sudo ln -s /usr/local/myprograms/luckybackup_script/lbprofile1 /usr/local/bin/lbprofile1
```Personally, I prefer to create symbolic links from the directory where I want the link - it makes more intuitive sense to me. So I'd do:

```
cd /usr/local/bin
sudo ln -s /usr/local/myprograms/luckybackup_script/lbprofile1 .

```Which will create the link with the same name as the destination file. (If you want to give your link a different name, simply put the name instead of the .

Steve.

---

### Post by Ralph L on 2010-07-10
Thank you very much.  I think you solved my problem.  It was so simple I feel embarrassed that I asked the question.  Oh, well.

Ralph

---

