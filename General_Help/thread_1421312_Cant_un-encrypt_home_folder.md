---
title: "Cant un-encrypt home folder"
date: 2010-03-04
forum: General Help
---

### Post by JamezQ on 2010-03-04
My problem is this [http://ubuntuforums.org/showthread.php?t=1421258](http://ubuntuforums.org/showthread.php?t=1421258).

I realise I signed up for this when I divided to install an alpha, and that's ok. I like seeing the development in action. Now it being crashed is not the problem, I can't recover my files because I choose to make my home folder encrypted. And I can't reach it from this live cd. 
```

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
```

So I try both, and clicking just opens terminal then closes it before I can see anything, so I enter the command and get this:
```
root@ubuntu:/media/38f015f5-fb00-4e96-af9b-29f95178278f/home/james#  ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

```

I can however login to ubuntu and although I cant get on gnome I can login though terminal and see my files, I don't know how to write select ones to my flash drive from terminal though. What would help me the MOST is some commands you guys can give me to run that you unencrypt my home folder while I am logged in to ubuntu in CLI. So I can then access my important files with this temporary live cd setup.

---

### Post by undecim on 2010-03-04
If you can log into the system, the easiest thing would be to copy all your files to an unencrypted folder. If you have more than half your hard drive space remaining (use "df -h" to check), you can copy them over. If you don't, you will have to move them.

```
sudo mkdir /home/rescue
sudo chown -u username
```
Then, if you have more than 50% free space:
```
cp -ar /home/username /home/rescue
```
If you dont have the free space:
```
mv /home/username /home/rescue
```
After running one of those commands run```
rm -r /home/.ecryptfs/undecim/.ecryptfs/auto-mount
```and then log out and back in.

After logging back in, run ```
sudo mv /home/rescue /home/username
```and all your files should be decrypted.

---

### Post by ben2talk on 2010-05-02
WTF???

so I log in as ben (which requires my /home/ben folder to be intact, and it's encrypted....)

then I sudo move (rename) my /home/ben folder to /home/whatever

then log out and log in... log in to what home folder???

Am I being silly? Isn't this problem all about having trouble with your home folder?

If you can log in I'd suggest you go into your /home/ben folder, and start copying the most important stuff first (don't forget ctrl-h to show hidden files) like your modified bashrc files, .Virtualbox, .conkyrc etc.

In addition (general thought) don't forget that if you modified your system, there's a ton of stuff in /usr/share directories that is worth backing up too.

I played the upgrade game a few times, and find that manually backing stuff up and doing fresh installs generally works best.  This latest Ubuntu 10.04 CD I burned actually logs out of X and presents me with a login screen (and I don't know the password!!) when I try anything (including typing 'ubuntu 10.04 live cd login' and clicking 'search' - instant logout!!!

---

