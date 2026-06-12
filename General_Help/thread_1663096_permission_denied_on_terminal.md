---
title: "permission denied on terminal"
date: 2011-01-09
forum: General Help
---

### Post by Zubeir on 2011-01-09
I am a new Ubuntu user. I was trying to install the mac4lin theme using the terminal and I was getting a permission denied message. How to solve the issue of permission? Or is there any other way to install the theme? In the appearance settings menu the install.sh of the theme is not recognized.

---

### Post by James_Lochhead on 2011-01-09
> **Zubeir said:**
> I am a new Ubuntu user. I was trying to install the mac4lin theme using the terminal and I was getting a permission denied message. How to solve the issue of permission? Or is there any other way to install the theme? In the appearance settings menu the install.sh of the theme is not recognized.

Hi Zubeir.

For security reasons programs do not have write permission outside of your own /home directory unless you explicitly give it to them by executing the program as the root user.

Simply preface the offending command with sudo in order to solve the problem by executing the command as the root user. So for example:

sudo mv /home/james/myExampleFile /myExampleFile 

Please note, however, that you should be careful as overusing the root is a security risk and can also cause some annoying problems if you're not careful (for example, you could delete every file on your computer with a simple typo); so remember to use it only when it's necessary.

---

### Post by ninjaaron on 2011-01-09
In addition to what James says about "sudo," it strikes me that you may also have to change the permissions on the install.sh script to executable.

navigate to the correct folder and type
```
chmod +x install.sh
```

I believe you can also do this in the file browser by right-clicking the script, clicking the permissions tab, and checking the "executable" box for the appropriate users/groups.

> **James_Lochhead said:**
> 
(for example, you could delete every file on your computer with a simple typo)

(whereas without sudo, you could only delete every file in your home-folder with a simple typo, which is no big deal, right?) ;)

---

