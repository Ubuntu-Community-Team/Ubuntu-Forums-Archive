---
title: "Software installation - BOINC????"
date: 2010-03-25
forum: General Help
---

### Post by LoneWolf_53 on 2010-03-25
I am running Ubuntu 9.10 64Bit and I used Synaptic to install BOINC on this system.

Being new there's much I haven't figured out yet and one of those things is how to install software that is not in Synaptic.

I've downloaded a much newer version of BOINC and have it residing on my desktop now.

It is 64Bit BOINC and the file is in the form of gnu.sh.

My question is how to I install this version on my computer?

What command do I need to use in the terminal?

Any guidance much appreciated.   Thank You.

---

### Post by TitanusEramius on 2010-03-25
Welcome over, and yes, a lot of things works different here.
If you have installed Boinc there is a shortcut in the menu Applications>System Tools and when you click it, it will launch the program you are used to from Windows.

If you have not installed Boinc yet, or are in doubt if you've done it right, this reading should help:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

I have installed and running Boinc from Synaptic without any problems, so if a program is listed in Synaptic I would definitely install it from there instead of getting it from the web. One of the many smart things in Synaptic is that each program (or package) have been checked to work probably and should not harm your system in any way, and when a package is installed through Synaptic, you can handle it with Synaptic (like uninstall or auto-update).

Good luck, and if you still struggle with Synaptic or Boinc after reading this, please write again.

---

### Post by LoneWolf_53 on 2010-03-25
Thank you for the reply.

Let me clarify I did install the BOINC client offered by Synaptic and that is what is running.

My problem is that since switching to Linux I've lost the ability to use my GPU's for crunching and part of that problem stems from the fact that the BOINC version offered in Synaptic is old.

The newer ones allow a person to utilized GPU resources as well so that is why I wanted to change to the Linux version I downloaded from the BOINC site but now that it's sitting on my desktop I don't know what to do with it.


I've asked the same question at my crunching team forum and it's been suggested I use getDeb so I suppose I'll have to investigate what that's about.

---

### Post by timgood on 2010-03-25
An updated version of Boinc for your computer is available at GetDeb [here]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=boinc") in .deb format.

Hope this helps.

---

### Post by LoneWolf_53 on 2010-03-25
OK I used getDeb and now have the latest version of BOINC installed and running.

Now I need to install the latest NVIDIA drivers along with CUDA.

I found a how too for Ubuntu 9.10 but when I get to step three in the virtual terminal and try to run the command as it's typed it doesn't work.

I'm guessing it may not be written for someone like myself who has no linux terminal experience.

The instructions are here............ [http://moelhave.dk/2009/12/nvidia-cuda-on-ubuntu-karmic-koala/](http://moelhave.dk/2009/12/nvidia-cuda-on-ubuntu-karmic-koala/)

I downloaded the files needed to my Desktop so would someone be so kind as to clue me in what the proper command is for the virtual terminal that will allow me to install the driver?

I thought Run was the command but apparently it's not.  :(

---

### Post by timgood on 2010-03-26
In step 3 make sure that you are in the same directory as the files you have downloaded. For example, if you have downloaded the files to a directory called 'Downloads' then type in terminal:

```
cd Downloads
```

which will change to the Downloads directory. You can verify you are there by using:

```
ls
```

which will give you a list of the files in that directory.

To run the installer file you will need to tell Ubuntu that the file you want to run is in the directory you are currently in, otherwise it will look for it elsewhere. To do that:

```
sudo ./cudadriver_2.3_linux_64_190.18.run
```

The './' tells the OS to use the file in the current directory - otherwise you will get a 'file not found' error.

Hope this helps.

---

### Post by oldos2er on 2010-03-26
I'm running Boinc with cuda; I never had to do anything beyond installing Boinc and the 190.53 nvidia drivers. Using Boinc manager v6.10.17.

---

### Post by LoneWolf_53 on 2010-03-26
> **timgood said:**
> In step 3 make sure that you are in the same directory as the files you have downloaded. For example, if you have downloaded the files to a directory called 'Downloads' then type in terminal:

```
cd Downloads
```which will change to the Downloads directory. You can verify you are there by using:

```
ls
```which will give you a list of the files in that directory.

To run the installer file you will need to tell Ubuntu that the file you want to run is in the directory you are currently in, otherwise it will look for it elsewhere. To do that:

```
sudo ./cudadriver_2.3_linux_64_190.18.run
```The './' tells the OS to use the file in the current directory - otherwise you will get a 'file not found' error.

Hope this helps.

I made sure I'm in the same directory.

I ran ls and the file name shows as  "cudadriver_3.0_linux_64_195.36.15.run"

I then typed in ```
sudo ./cudadriver_3.0_linux_64_195.36.15.run
``` after pressing enter I get  "Command not found"????????????????

What am I missing here?

---

### Post by oldos2er on 2010-03-26
> **LoneWolf_53 said:**
> What am I missing here?

Did you make it executable first? ```
chmod a+x cudadriver_2.3_linux_64_190.18.run
```

---

### Post by LoneWolf_53 on 2010-03-26
> **oldos2er said:**
> Did you make it executable first? ```
chmod a+x cudadriver_2.3_linux_64_190.18.run
```

Well it took a while but I finally got the drivers installed.  :)

The issue was that the code in the instructions I was following should have read
```
sudo sh cudadriver_2.3_linux_64_190.18.run
```Doing that worked for me.

I'm sort of beginning to see that as appreciated as some people's tutorials are there's an overall tendency to assume a certain level of knowledge on the part of the user.

Though I sort of understand that the fact is we all have to begin to learn somehow so if someone is going to post a code it would be good to ensure that it's accurate and complete or not even bother.

As it stands now I'm a bit shy to follow some directions as I have no idea as to whether they are correct or not.

I did take the time to print out a list that gave some of the commands used in a terminal but even there I'd have to be further along than I am to grasp what some of them are for.

I find it easier to learn by applying code instructions that I find as they start to make sense after a while.  :)

---

### Post by oldos2er on 2010-03-26
> **LoneWolf_53 said:**
> I'm sort of beginning to see that as appreciated as some people's tutorials are there's an overall tendency to assume a certain level of knowledge on the part of the user.


I'm sure that's true, particularly when someone posts outside of the Absolute Beginners forum.

---

