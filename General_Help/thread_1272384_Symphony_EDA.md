---
title: "Symphony EDA"
date: 2009-09-22
forum: General Help
---

### Post by bcpaes on 2009-09-22
Hi everyone. I Study computer engineering and I needed a software to compile VHDL. A friend of mine told me about Symphony EDA [(http://www.symphonyeda.com]("http://www.symphonyeda.com/")).

I did all the instructions that were listed on the site. However the installation ask me to change some settings in Ubuntu that are dubious to me.

Here is what I`ve done:

1. Untar the download file to /home/bruno/symphony
2. Ran the command > sudo ./install.sh3. > Please enter installation directory for VHDL Simili 3.1
[default = /usr/local/Simili31] : 
 Said yes
4. > You have just installed VHDL Simili. Please add the following commands
to your shell initialization file (~/.bashrc or ~/.cshrc or ~/.profile)
(see the Installation chapter in the documentation for more details)
 
bash, sh users:
    export SYMPHONYEDA="/usr/local/Simili31"
    . "$SYMPHONYEDA/bin/init.sh"
 
csh users:
    setenv SYMPHONYEDA "/usr/local/Simili31"
    source "$SYMPHONYEDA/bin/init.csh"
 
VHDL Simili uses FLEXlm to manage licenses. Please read the License Management
setup instructions for Unix in the following documentation (chapter 3).
You do not need special licenses for the FREE edition unless you are
installing from a very old distribution (please download newer version).
 
-rw-r--r-- 1 500 users    3253 2008-04-01 00:58 /usr/local/Simili31/doc/index.htm
-rw-r--r-- 1 500 users 1379575 2008-04-01 00:58 /usr/local/Simili31/doc/similiumanual.pdf
 
The VHDL Simili toolset primarily consists of the following commands:
 
1. sonata     -- Graphical User Interface for Simili (uses any available license)
2. sonatastd  -- Same as above except it requires the Std. Edition license
3. sonatapro  -- Same as above except it requires the Prof. Edition license
4. vhdlp      -- This is the command-line VHDL compiler
5. vhdle      -- This is the command-line VHDL simulator
 
You can use the following command to request licenses (demo or purchased):
(please run the license request as root)
 
    sonata -L
 
If you are a new user of sonata, it will be very helpful for you to go
through the tutorial (approx. 15-30 minutes) included in the documentation.
--------------------------------------------------------------------------
Thank you for trying out VHDL Simili. Good Bye.But I do not know what is "my shell initialization files" or the type of user I am. 
The program is not in the applications menu. How to add?

Thanks and sorry for the bad english

---

### Post by bogdan.veringioiu on 2009-09-22
Hi.
You are an ubuntu user, therefore you are a bash user.
So, you can do this:

-open a terminal
-type gedit ~/.bashrc
-add the following 2 lines at the end of the file, and save:

export SYMPHONYEDA="/usr/local/Simili31"
. "$SYMPHONYEDA/bin/init.sh"

I don't know if this software will work for you without license.
However, after you make the above mods, open a new terminal, and type sonata. (it looks to me that this is the gui for your program, while vhdlp and vhdle are command line compilers/simulators).
Maybe it is necessary to run sudo sonata -L, for license...

Bogdan

---

### Post by bcpaes on 2009-09-22
Thanks! Worked great when I type in the terminal
> sonata

But, i want to put a shotcurt to the main menu. And it doesen't work.... 

> Type: application
       Name: Symphony EDA
       Command: sonata
       Comments:

And then when I press the shotcurt this is the message i recive:

Can't execute "Symphony EDA"
Failed to execute child process
"sonata" (non-existent file or directory)

---

### Post by bogdan.veringioiu on 2009-09-22
I think your menu entry should work after a reboot (.profile will be read).

Let me know.

---

### Post by bcpaes on 2009-09-22
nothing.... any suggestions?

---

### Post by rossmoore on 2009-09-22
Well, it **could** be the sonata hasn't installed fully. Do you have a file in your home directory called sonata? If so, you can make your launcher work by changing the "Command" entry to:
~/sonata
(presuming you're the only user on your computer) Does that work? It's just a guess.

---

### Post by bogdan.veringioiu on 2009-09-23
Ok.

Is it still working from the terminal?
Try these steps:
1)edit .profile
gedit ~/.profile
Add the same lines that you did in .bashrc, at the end:
export SYMPHONYEDA="/usr/local/Simili31"
. "$SYMPHONYEDA/bin/init.sh"
Reboot and try your menu entry.
If not works try the next step:
2)create a .sh file that will be your launcher:
gedit start_sonata.sh
Paste the following lines:
#!/bin/sh
export SYMPHONYEDA="/usr/local/Simili31"
. "$SYMPHONYEDA/bin/init.sh"
sonata

Save the file somewhere in your home directory.
Then make it executable. After this, edit your menu entry, and as command, put the above created file (with path). Ex: /home/<youruser>/start_sonata.sh

Try and let me know.
Bogdan

---

