---
title: "Tar.gz Help"
date: 2011-04-26
forum: General Help
---

### Post by hijiz on 2011-04-26
Hi I know their must be over a million threeads to help answer this but i do not understand how to install tar.gz files im trying to install metsploit and i followed the instructions here [http://dev.metasploit.com/redmine/projects/framework]("http://dev.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu")
> **Metasploit Framework**

       Once the dependencies have been installed, download the Unix tarball from the [download page]("http://www.metasploit.com/framework/download/") and run the following commands:

[QUOTE]$ tar xf framework-3.X.tar.gz
$ sudo mkdir -p /opt/metasploit3
$ sudo cp -a msf3/ /opt/metasploit3/msf3
$ sudo chown root:root -R /opt/metasploit3/msf3
$ sudo ln -sf /opt/metasploit3/msf3/msf* /usr/local/bin/       When you've completed this step, you should have a working  installation and be able to run modules, pivot through compromised  systems, and use most of the Metasploit Framework's features.  The  following optional installation steps will give you extra functionality.
[/QUOTE]

But i reach a stand still after downloading the unix tarbal what do i do.

---

### Post by gandaran on 2011-04-26
> **hijiz said:**
> Hi I know their must be over a million threeads to help answer this but i do not understand how to install tar.gz files im trying to install metsploit and i followed the instructions here [http://dev.metasploit.com/redmine/projects/framework]("http://dev.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu")


But i reach a stand still after downloading the unix tarbal what do i do.
very simple, you don't need to compile anything here, its just a mater of extracting the tarball then make installation directory and copy the files to the directory.
to begin, install the dependencies and download the tarball to your home/user directory then open up the terminal and (copy/paste) run the commands one at a time from the top, thats all, the instructions are very simple.
if you get any errors running the commands please post them here.

---

### Post by WorMzy on 2011-04-26
> But i reach a stand still after downloading the unix tarbal what do i do.

You'll need to open a terminal (Applications -> Accessories -> Terminal), then use cd to navigate to the directory containing the tarball you just downloaded. e.g.```
cd /home/username/Downloads
```

Then follow the instructions.

---

### Post by hijiz on 2011-04-27
Ive tried both however i get the following
> emilio@emilio-Aspire-one:/home$ tar xf framework-3.X.tar.gz
tar: framework-3.X.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
emilio@emilio-Aspire-one:/home$ 


---

### Post by nothingspecial on 2011-04-27
Try 

```
cd ~/Downloads
```

first.

You are in **THE** home directory, not **YOUR** home directory.

---

### Post by hijiz on 2011-04-27
i reached the downloads directory but then...
> emilio@emilio-Aspire-one:~$ cd ~/Downloads
emilio@emilio-Aspire-one:~/Downloads$ tar xf framework-3.X.tar.gz
tar: framework-3.X.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
emilio@emilio-Aspire-one:~/Downloads$ 


---

### Post by nothingspecial on 2011-04-27
Where is it?

You need to cd to there

```
cd ~/Desktop 
```         maybe

---

### Post by WorMzy on 2011-04-27
I think I can see the problem here, the instructions are telling you to run

```
tar xf framework-3.X.tar.gz
```

but you're not supposed to take that quite so literally, the X is there as a place-holder for the rest of the version number. The actual command would be

```
tar xf framework-3.6.0.tar.bz2
```

---

### Post by hijiz on 2011-04-27
Its in downloads

---

### Post by hijiz on 2011-04-27
Wormzy
I thougt so to earlier but when i did it...
> emilio@emilio-Aspire-one:~/Downloads$ tar xf framework-3.6.0.tar.bz2
tar: framework-3.6.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
emilio@emilio-Aspire-one:~/Downloads$ 


---

### Post by gandaran on 2011-04-27
> **hijiz said:**
> Wormzy
I thougt so to earlier but when i did it...
well if you are having  this trouble with the first command why not skip it! just right click the tarball and extract it then carry on with the second command.

---

### Post by WorMzy on 2011-04-27
Like Gandaran said, maybe it'd be easier for you to extract the contents of the archive via the GUI. Just open nautilus (the file browser), open your Downloads folder, right-click the archive, and choose "Extract Here".

Once that's done:
press Ctrl+L
copy the address from the address bar
open a terminal
type "cd " (without the quotes)
then press ctrl+shift+v to paste the directory's address
then press enter
then follow the rest of the instructions (skipping the tar instruction)

---

### Post by hijiz on 2011-04-27
ive tried extracting it twice and an error ocurs

---

### Post by hijiz on 2011-04-27
Ive tried a third and a fourth time it happened again and it wont tell me what the error is.

---

### Post by gandaran on 2011-04-27
> **hijiz said:**
> Ive tried a third and a fourth time it happened again and it wont tell me what the error is.
maybe the package is corrupted, try downloading it again.

edit;
I checked the linux download link and the package is "framework-3.6.0-linux-mini.run", so it's not a tarball, so what do you really have in the downloads folder?

---

### Post by btindie on 2011-04-27
Which package did you actually download?

The Linux package is in fact a .run file which is meant to be executed, see the [generic]("http://dev.metasploit.com/redmine/projects/framework/wiki/Install_Linux") install instructions, where as the Unix package is a tar.gz archive.

If you read the Ubuntu install instructions it says to download the Unix package
> Once the dependencies have been installed, download the **Unix tarball** from the [download page]("http://www.metasploit.com/framework/download/") and run the following commands:So download it again and do the following
```
$ cd ~/Downloads
$ wget "http://updates.metasploit.com/data/releases/framework-3.6.0.tar.bz2"
$ tar jxvf framework-3.6.0.tar.bz2
```then follow the normal instructions after the **tar** command.

---

### Post by hijiz on 2011-04-27
I Will download the file again and try to extract it again i will tell you how it went.

---

### Post by hijiz on 2011-04-27
I tried doing as gandaran and WorMzy proposed it didnt work nothing happened at all. however i will try again as originally instructed thanks alot to everyone.

---

### Post by hijiz on 2011-04-27
Still not working just like the beggining.

---

### Post by WorMzy on 2011-04-27
I recommend that you follow btindie's instructions. In fact, here's a one-liner which does the same thing, but saves you having to press enter three times.

```
cd ~/Downloads && wget "http://updates.metasploit.com/data/releases/framework-3.6.0.tar.bz2" && tar jxvf framework-3.6.0.tar.bz2
```

If it works, you should see a lot of text scroll past very quickly, don't panic when you see that, it's just the contents of the archive being extracted.

---

### Post by hijiz on 2011-04-27
I just did what btindie said the commands worked however when i procede to step 2 it ask for sudo password i type my password and then nothing happens is this what happens is there some thing wrong?

---

### Post by WorMzy on 2011-04-27
Yeah, "mkdir" just makes a directory, then returns you to the prompt; it looks like nothing has happened, but that's normal.

In fact, you probably won't see any feedback from any of the other commands, unless they don't work for some reason.

---

### Post by btindie on 2011-04-27
The sudo command is just to allow you to run commands that require root privileges to operate. Those commands won't generate any output.

If you've run those commands then you should now have a load of files in /opt/metasploit3
```
$ ls /opt/metasploit3
```

---

### Post by hijiz on 2011-04-27
all the other commands after mkdir are similiar to mkdir what i mean is nothing happens for a while the terminal jumps to another line wich stays completly blank for a while an then the emilio@emilio-Aspire-one:~/Downloads$ shows up. but nothing happens i dont see metasploit in the aplicatoins menu does this download include GUI or not?

---

### Post by hijiz on 2011-04-27
if i type metasploit in terminal it says command not found so i believe the instalation did not work please some one help

---

### Post by hijiz on 2011-04-27
and btindie you are wrong there is only one msf3.
> emilio@emilio-Aspire-one:~$ ls /opt/metasploit3
msf3
emilio@emilio-Aspire-one:~$ 


---

### Post by WorMzy on 2011-04-27
```
metasploit
```

won't work, but msfcli, msfconsole, msfd, msfelfscan, msfencode, msfgui, msfmachscan, msfopcode, msfpayload, msfpescan, msfrpc, msfrpcd, and msfupdate should.

Try 
```
msfgui
```

---

### Post by hijiz on 2011-04-27
wow thanks that did the trick thank you.

---

