---
title: "What is bashrc"
date: 2012-01-27
forum: General Help
---

### Post by Sachin_ruk on 2012-01-27
Hi all,

I am installing Cuda right now and trying to make sense of the following. Also what exactly is bashrc?

Once you have completed installing this, add the CUDA bin location to your path - I did this in my .bashrc .
export PATH=$PATH:/usr/local/cuda/bin

I ran the above export... part on terminal- is that what I was supposed to do?

Thanks,
Sachin

---

### Post by yetiman64 on 2012-01-27
1. Open your home folder and use CTRL + H to show hidden files/folders. 

2. Look for and open in gedit the file .bashrc.

3. Add the line with the export command to the very end of the file in a new line. Save the file and exit gedit.

4. Close any open terminals. Open a new terminal and paste in the command ```
echo $PATH
``` your path to /usr/local/cuda/bin should now show at the end of the system PATH. If it is, your /usr/local/cuda/bin scripts/executables are now usable from the terminal directly. If not, log out and back in, and retry the "echo $PATH" command again.

---

### Post by kjohri on 2012-01-28
.bashrc is the file that is executed when you open a terminal window (like gnome terminal) for text-based interaction with the system from the command line. You should open the file .bashrc in your home directory in a text editor program like vi or gedit and add the line, 

export PATH=$PATH:/usr/local/cuda/bin

at the end of this file and save the file. After that you can close the terminal window. The effect of this will be that the directory /usr/local/cuda/bin is added to your PATH whenever you open a new terminal window next. You can check this by opening a new terminal window and giving the command,

echo $PATH

---

### Post by Habitual on 2012-01-28
apropos path

---

