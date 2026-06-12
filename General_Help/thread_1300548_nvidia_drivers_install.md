---
title: "nvidia drivers install"
date: 2009-10-25
forum: General Help
---

### Post by ChrnoXIII on 2009-10-25
hi guys,

im totally new to linux, though i am a proficient windows user...

anyway i just installed 9.04 on my computer through wubi.
i tried to install the latest nvidia drivers on linux.
i downloaded it and tried to run it --> it tells me i need root access... okay... i do some research..

now i go into the terminal and go "sudo sh [nvidia driver filename].run"

this prompts me to input a [sudo] password. so i type in my login password as it is the only one i've set for ubuntu.

it denies me...
can anyone offer some help?
i also tried stopping the gdm with "sudo /etc/init.d/gdm stop" and tried the same process but it does not work > <

thanks in advance

---

### Post by P4man on 2009-10-25
go to system > administration > hardware drivers

Use the recommended one. If nothing is listed, then tell us what videocard you have. Unlike with windows, downloading drivers from the manufacturer is a last resort option.

---

### Post by ChrnoXIII on 2009-10-25
hi i have a nvidia 9300m running on my laptop

i looked in that hardware drivers place first and it shows nothing
i also have not updated ubuntu if that makes a difference

---

### Post by P4man on 2009-10-25
thats odd. It should prompt you to install restricted nvidia drivers for that card. Are you connected to the internet?

As for the updates, I would think thats not necessary unless perhaps that card is newer than ubuntu 9.04 which would surprise me. I guess it wouldnt hurt trying.

---

### Post by ChrnoXIII on 2009-10-25
yup i can connect to the internet but i am behind a proxy (i entered the proxy settings into ubuntu).

---

### Post by ChrnoXIII on 2009-10-25
lol? when i try to update it it starts to download them but the 'status' of all the downloads is failed...
urgh... is it because im running wireless?

---

### Post by P4man on 2009-10-25
no its the proxy
You probably only configured it for your browser. One way or another, the package manager (and updates and therefore the driver isntaller) are not using it.

Perhaps this helps:
[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320)

edit: open synaptic package manager from system > administration. Then go edit / preferences /network and fill out the proxy. If you already did that and its not working, see above link

---

### Post by ChrnoXIII on 2009-10-25
well i went to system>prefs>network proxy and applied all the settings there. and then i clicked apply settings globally... it should work? O.o

---

### Post by P4man on 2009-10-25
I guess it should, but doesnt.
Try it in synaptic anyway, if that solves it we'll open a bug report.

---

### Post by ChrnoXIII on 2009-10-25
sorry, but try what in synaptics? i have it opened and i pressed reload, same deal (all the status of the downloads are "failed")

---

### Post by P4man on 2009-10-25
sorry maybe you missed my edit. this part:

open synaptic package manager from system > administration. Then go edit / preferences /network and fill out the proxy. If you already did that and its not working, see above link

---

### Post by dv3500ea on 2009-10-25
You downloaded the *.run file from the site right?

Save the *.run file from the site into a directory (I will assume /home) then press CTRL-ALT-F1 this should bring up a full screen black and white command line. 
Run these commands:
```

cd /home
  sudo /etc/init.d/gdm stop
  sudo chmod +x *.run
  sudo ./*.run

```It should go through an installer where you need to accept the EULA then will return to the command line.
Enter this:
```

sudo /etc/init.d/gdm start

```to restart the graphical user interface.
If you want to enable visual effects go to system->preferences->startup and add the command 'compiz' to the list. Next, open a terminal (ALT-F2 type 'gnome-terminal') and run:
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by DeMus on 2009-10-25
> **ChrnoXIII said:**
> hi guys,

im totally new to linux, though i am a proficient windows user...

anyway i just installed 9.04 on my computer through wubi.
i tried to install the latest nvidia drivers on linux.
i downloaded it and tried to run it --> it tells me i need root access... okay... i do some research..

now i go into the terminal and go "sudo sh [nvidia driver filename].run"

this prompts me to input a [sudo] password. so i type in my login password as it is the only one i've set for ubuntu.

it denies me...
can anyone offer some help?
i also tried stopping the gdm with "sudo /etc/init.d/gdm stop" and tried the same process but it does not work > <

thanks in advance

Just follow these simple rules to get the latest nVidia driver around:

Dowload from this website: [_nVidia drivers_]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/") the files suited for Jaunty and suited for your OS type (32 or 64 bits, I use 64 so I downloaded the 64 bits files):
Code:

```
nvidia-190-kernel-source_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-libvdpau_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-modaliases_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-glx-190_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
```

After download, open nautilus and go to the download folder. One by one you double click the .deb files and they will be installed automatically by gdebi. Do it in the order as the files are written above. That way all dependencies will be okay.

Then after a reboot all will be fine and you have the latest nVidia proprietary driver.

---

### Post by P4man on 2009-10-25
guys, apt-get is not getting through the proxy for him. While he can download and isntall nvidia drivers manually, there is no reason for him to do so and he should fix the apt / proxy issue or he wont be able to install or update anything.

---

### Post by ChrnoXIII on 2009-10-25
hi i havent tried doing it manually, but yea i did already put the proxy settings in and tried to update again with no luck

*edit sorry yeah it works now... strange that setting the proxy in system>preferences>proxy settings doesnt set it in synaptics...

updating now

*edit yea everything works fine now, sorry for the trouble and thanks for your help! i can see the 180 nvidia drivers in "hardware drivers"

---

### Post by P4man on 2009-10-25
The above posters mean well, but you really need to get this fixed or you wont be able to do any updates or install anything the normal way and life will be hell :)

Try openining synaptic again. Go to settings > repositories. You will see the download from drop down. Select other, then select best server. Perhaps your proxy is also blocking some stuff.

While you try that Ill see if I can find out how to force a proxy in apt.

edit: posts crossed. Glad you solved it. Dont forget to mark the thread as SOLVED once it works :)

---

### Post by P4man on 2009-10-25
one more thing. Now that it works, let me give you the answer to your actual question in your first post. If you download something in linux, you can not execute it as a program until you change the permissions. All you had to do was right click it, go to properties,  permissions and enable "allow executing file as program". Then what you did would have worked.

But its much better to install those drivers automatically as you did now, it will save you from headaches when you do a kernel upgrade (which will break a manually installed driver, forcing you to either reinstall the driver of recompile the kernel modules each time). Unless nvidia drivers come with DKMS support, im not entirely sure about that.

---

### Post by grndzro on 2009-10-25
download NVIDIA-Linux-x86_64-190.42-pkg2.run  
From here [http://www.nvnews.net/vbulletin/showthread.php?p=2105790](http://www.nvnews.net/vbulletin/showthread.php?p=2105790)
Just right click the link in the first post and save to desktop

Type "sudo telinit 1" to kill the xserver then type "sudo telinit 3" in Terminal to resume, This will stop xserver so write down anything you will need.

Then navigate to your folder hat has NVIDIA-Linux-x86_64-190.42-pkg2.run in it. itl be something like cd home/Desktop, or cd .. yada yada you might need to fool around with the dir command

Type Sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run , Then follow the prompts

---

### Post by DeMus on 2009-10-25
> **grndzro said:**
> download NVIDIA-Linux-x86_64-190.42-pkg2.run  
From here [http://www.nvnews.net/vbulletin/showthread.php?p=2105790](http://www.nvnews.net/vbulletin/showthread.php?p=2105790)
Just right click the link in the first post and save to desktop

Type "sudo telinit 3" in Terminal, This will stop xserver so write down anything you will need.

Then navigate to your folder hat has NVIDIA-Linux-x86_64-190.42-pkg2.run in it. itl be something like cd home/Desktop, or cd .. yada yada you might need to fool around with the dir command

Type Sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run , Then follow the prompts

This is a release candidate and as such does not have to be stable.
Stick to 190.36 as I described in my first post in this thread.

---

### Post by grndzro on 2009-10-26
lol looking at peoples problems it seems the 190.36 are not as stable as the 190.42's.

And installing them in the terminal is generally better since xserver is picky about running and installing drivers at the same time.

Just be sure to remove any other drivers that may be present.

---

