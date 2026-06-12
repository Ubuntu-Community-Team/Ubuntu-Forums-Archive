---
title: "After nvidia updates from Ubuntu-X-Swat X-Updates, Can't login"
date: 2012-07-31
forum: General Help
---

### Post by diego898 on 2012-07-31
Hello,

I've installed Ubuntu 12.04. I added the Ubuntu-X-Swat X-Updates repository and ran

sudo apt-get update
sudo apt-get upgrade

I blindly pressed ok (stupid I know!) and then restarted. Now I can't login it to my account, even though my password is correct. It goes to a black screen as if its tryign to log me in, then it returns me to the login screen. Even when I change my window manager to Ubuntu 2D, Gnome, Gnome Classic, Gnome Classic (No effects) by clicking the symbol next to my name, the same thing happens. What is very strange however, is that **I can still login using the guest account! **

I thought I should try uninstallting all packages that came from that repository (finding them using [the method described here]("http://askubuntu.com/questions/37531/how-do-i-remove-all-packages-from-a-certain-repository")), remove the repository, and re-install nvidia-common but I can't because I can only access the guest account, and I cant su into anything.

Any help would be great!

---

### Post by diego898 on 2012-08-01
I've since booted into recovery mode, removed nvidia-common, and installed the current version of nvidia-common listed here: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/)
which is 295.40-0ubuntu1 using the following command:

```
apt-get install nvidia-common=295.40-0ubuntu1
```

I then tried to login again and it still did not work. I can still login through the guest user however. And in that user, I verify that the currently installed version is indeed 295.40. So now I'm really stumped!

---

### Post by diego898 on 2012-08-01
I've also removed my xorg.conf file to try and see if that helps, but it did not.

---

### Post by bogan on 2012-08-01
Hi!, **diego898,**

According to Synaptic ' nvidia- common ' is a progam to: " Find obsolete NVIDIA drivers"!!

What you are looking for is 'nvidia-current'.

Please Post: > sudo apt-cache policy nvidia-currentChao!,** bogan**.

---

