---
title: "Eclipse path"
date: 2010-02-27
forum: General Help
---

### Post by talhaguy on 2010-02-27
Hey everyone,

I installed the Eclipse IDE on my desktop. I want to be able to run it when I press Alt+F2 and type eclipse. But when I do that it just opens the folder where the executable is. The folder is in my home folder, by the way. So, I think this is a problem with my path. Can anyone help me change it so that the Eclipse application will start instead of the folder?

Thanks.

---

### Post by dondiego2 on 2010-02-27
> **talhaguy said:**
> Hey everyone,
I installed the Eclipse IDE on my desktop. 


I read the subject line and thought you were looking for an astronomical eclipse path :P

---

### Post by spiderbatdad on 2010-02-27
tried eclipse a couple of years ago, so not very up to speed on using it, but if you look at the hidden file .profile in your home directory, you will see how /home/bin is exported to $PATH if the directory exits. You should be able to simply add to the end of the .profile file:
```
PATH="$HOME/eclipse:$PATH"
```Directory names are case sensitive, and you may end up having to further edit profile to something like:
```
export PATH=$PATH:$HOME/eclipse/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/eclipse/lib
``` Sorry just guessing.

---

### Post by talhaguy on 2010-02-27
@dondiego2: Haha, probably should've been more specific in the title.



export PATH=$PATH:$HOME/eclipse/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/eclipse/lib

Could I get an explanation of what this code is doing?

---

### Post by spiderbatdad on 2010-02-27
normally this would go into .bashrc rather than .profile, and .bashrc maybe a better choice.
The command is to add the directory /home/eclipse/bin to the users $PATH: this being where bash look for executable files...to the best of my limited understanding.
For example if you simply type ```
$PATH
``` into your terminal you will get a list of directory where bash will execute files for the user just by entering the program name. After the above command, the user will also be able to type eclipse and execute the program...or presumably if your launcher points to /home/eclipse, it will also work.

The second command attempts to add specific libraries used by eclipse, assuming there is a lib directory in /home/eclipse, to path of library dependencies.

Sorry I havent used eclipse in a long time. It was fun though and worked well, so I know you can get it going. Could have let you wait to someone who knows how to get it going comes along, but this is something to try in the meantime. It will not hurt your system.

The actual PATH to export that is $HOME/eclipse/bin will depend on the directory structure in the eclipse folder...is there an executable in the directory or is it in another directory called bin.../home/eclipse/bin/<executable>

---

### Post by spiderbatdad on 2010-02-27
Have you seen the community documentation on eclipse?
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

