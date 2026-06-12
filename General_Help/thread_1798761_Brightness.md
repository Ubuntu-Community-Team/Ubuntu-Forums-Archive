---
title: "Brightness?"
date: 2011-07-06
forum: General Help
---

### Post by iRide113 on 2011-07-06
Hi,

Coming from Windows 7. Long time Mac user too.


Problem is I can't adjust screen brightness. When I push the shortcut keys on my computer, it shows the little brightness thing in the right corner, but even though it shows it changing, the actual screen brightness does not change.

Dell Inspiron 17R
Intel i5
64 Bit

11.04

---

### Post by iRide113 on 2011-07-06
Bump...

---

### Post by Toz on 2011-07-06
Things to try:

1. Kernel parameters (see: [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot") for instructions on how to try them temporarily). Try the parameters:
- **acpi_backlight=vendor**
- **acpi_osi=**
- **acpi_osi=\"Linux\"**

If they don't work...

2. Boot normally (without the above kernel parameters), open up a terminal window, type in the following commands, and post back the results:
```
cat /sys/class/backlight/acpi_video0/brightness
```
```
ls /sys/class/backlight
```
```
lspci | grep VGA | cut -d' ' -f1
```

We can try to implement the script at: [http://ubuntuforums.org/showpost.php?p=10926719&postcount=6]("http://ubuntuforums.org/showpost.php?p=10926719&postcount=6"), but we'll need to be sure we have the right info in the script for your system.

---

### Post by iRide113 on 2011-07-07
Didn't work so here you go.

> 
```
cat /sys/class/backlight/acpi_video0/brightness
```

     ```
cat: /sys/class/backlight/acpi_video0/brightness: No such file or directory
```

> 
```
ls /sys/class/backlight
```

     ```
[COLOR="DeepSkyBlue"]dell_backlight[/COLOR]
```

> 
```
lspci | grep VGA | cut -d' ' -f1
```

     ```
00:02.0
```

---

### Post by Toz on 2011-07-07
What does:
```
cat /sys/class/backlight/dell_backlight/brightness
```return?

And what video card do you have?
```
lspci | grep VGA
```

---

### Post by iRide113 on 2011-07-07
> **Toz said:**
> What does:
```
cat /sys/class/backlight/dell_backlight/brightness
```return?

```
15
```

> 
And what video card do you have?
```
lspci | grep VGA
```
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

```

---

### Post by Toz on 2011-07-07
Since you're maximum brightness value is 15, lets edit the script a bit.

Create a file called **backlight_d.sh**:
```
sudo gedit /usr/local/bin/backlight_d.sh
```

With the following contents:
```

#!/bin/sh

old_b='15';

while : ; do
  b=`cat /sys/class/backlight/dell_backlight/brightness`;

  if [ $old_b != $b ]; then
    case $b in
      0) hex_b=00 ;;
      1) hex_b=11 ;;
      2) hex_b=22 ;;
      3) hex_b=33 ;;
      4) hex_b=44 ;;
      5) hex_b=55 ;;
      6) hex_b=66 ;;
      7) hex_b=77 ;;
      8) hex_b=88 ;;
      9) hex_b=99 ;;
      10) hex_b=aa ;;
      11) hex_b=bb ;;
      12) hex_b=cc ;;
      13) hex_b=dd ;;
      14) hex_b=ee ;;
      15) hex_b=ff ;;
      *) hex_b=ff ;;
    esac
    old_b=$b
    setpci -s 00:02.0 F4.B=$hex_b
  fi

  sleep 0.5
done

```

Make the script executable:
```
sudo chmod +x /usr/local/bin/backlight_d.sh
```

Then start it up with root privileges:
```
sudo nohup /usr/local/bin/backlight_d.sh &
```

Now test the brightness controls.

---

### Post by iRide113 on 2011-07-07
> **Toz said:**
> Since you're maximum brightness value is 15, lets edit the script a bit.

Create a file called **backlight_d.sh**:
```
sudo gedit /usr/local/bin/backlight_d.sh
```

With the following contents:
```

#!/bin/sh

old_b='15';

while : ; do
  b=`cat /sys/class/backlight/dell_backlight/brightness`;

  if [ $old_b != $b ]; then
    case $b in
      0) hex_b=00 ;;
      1) hex_b=11 ;;
      2) hex_b=22 ;;
      3) hex_b=33 ;;
      4) hex_b=44 ;;
      5) hex_b=55 ;;
      6) hex_b=66 ;;
      7) hex_b=77 ;;
      8) hex_b=88 ;;
      9) hex_b=99 ;;
      10) hex_b=aa ;;
      11) hex_b=bb ;;
      12) hex_b=cc ;;
      13) hex_b=dd ;;
      14) hex_b=ee ;;
      15) hex_b=ff ;;
      *) hex_b=ff ;;
    esac
    old_b=$b
    setpci -s 00:02.0 F4.B=$hex_b
  fi

  sleep 0.5
done

```

Make the script executable:
```
sudo chmod +x /usr/local/bin/backlight_d.sh
```

Then start it up with root privileges:
```
sudo nohup /usr/loca/bin/backlight_d.sh &
```

Now test the brightness controls.

Think I am doing something wrong...

I execute the first command.

Paste the second code into the file.

Save it.

Open a new terminal.

Then when I type:
```
sudo chmod +x /usr/local/bin/backlight_d.sh
```
I get asked for my password and then nothing, just a new line.

And then when I type this:
```
sudo nohup /usr/loca/bin/backlight_d.sh &
```
I get:
```
[1] 3535
tony@Tony-Inspiron17R-Ubuntu:~$ nohup: ignoring input and appending output to `nohup.out'
nohup: failed to run command `/usr/loca/bin/backlight_d.sh': No such file or directory

```

---

### Post by Toz on 2011-07-07
oops, typo. Last command should be:

**sudo nohup /usr/local/bin/backlight_d.sh &**

---

### Post by iRide113 on 2011-07-07
> **Toz said:**
> oops, typo. Last command should be:

**sudo nohup /usr/local/bin/backlight_d.sh &**

I get
```
[1] 5327
root@Tony-Inspiron17R-Ubuntu:/home/tony# nohup: ignoring input and appending output to `nohup.out'

```

And after typing that, and push the display buttons on my keyboard, no change in brightness still.

---

### Post by Toz on 2011-07-08
Hmmm. Lets try a couple of other commands and see if it makes a change.

As root:
```
setpci -s 00:02.0 F4.B=77
```
```
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness
```

If neither make a change, perhaps you can give Kamal Mostafa's PPA a try: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight") - just had a look and there have been reports that it successfully fixes the problem with the Dell 17R.
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight 
sudo apt-get update
```
You should now have a new kernel available and as per the info there, a new gnome-power-manager.

---

### Post by elianto on 2011-07-08
Hello looks like I have the same problem... It was working before in Natty up to the other day when I was reading on late night and I've set the brightness to minimum, and now I can't bring it back to normal values.
I tried what you suggested in this thread (not the ppa since I have an ATI card) but unfortunately  nothing worked up to now now the details:
It's a dell studio xps 16

```
 lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Device 9488

cat /sys/class/backlight/acpi_video0/brightness
15
ls /sys/class/backlight
acpi_video0

cat bin/backlight.sh                                                                                                                                                                        

#!/bin/sh
                                                                                                                                                                                            
old_b='15';                                                                                                                                                                                 
vga=$(lspci | grep VGA | cut -d' ' -f1)                                                                                                                                                     
while : ; do                                                                                                                                                                                
  b=`cat /sys/class/backlight/dell_backlight/brightness`;                                                                                                                                   
                                                                                                                                                                                            
  if [ $old_b != $b ]; then                                                                                                                                                                 
    case $b in                                                                                                                                                                              
      0) hex_b=00 ;;                                                                                                                                                                        
      1) hex_b=11 ;;                                                                                                                                                                        
      2) hex_b=22 ;;                                                                                                                                                                        
      3) hex_b=33 ;;                                                                                                                                                                        
      4) hex_b=44 ;;                                                                                                                                                                        
      5) hex_b=55 ;;                                                                                                                                                                        
      6) hex_b=66 ;;                                                                                                                                                                        
      7) hex_b=77 ;;                                                                                                                                                                        
      8) hex_b=88 ;;                                                                                                                                                                        
      9) hex_b=99 ;;                                                                                                                                                                        
      10) hex_b=aa ;;                                                                                                                                                                       
      11) hex_b=bb ;;                                                                                                                                                                       
      12) hex_b=cc ;;                                                                                                                                                                       
      13) hex_b=dd ;;                                                                                                                                                                       
      14) hex_b=ee ;;                                                                                                                                                                       
      15) hex_b=ff ;;                                                                                                                                                                       
      *) hex_b=ff ;;                                                                                                                                                                        
    esac                                                                                                                                                                                    
    old_b=$b                                                                                                                                                                                
    echo "setpci -s $vga F4.B=$hex_b"                                                                                                                                                       
    setpci -s $vga F4.B=$hex_b                                                                                                                                                              
fi                                                                                                                                                                                        
                                                                                                                                                                                            
  sleep 0.5                                                                                                                                                                                 
done

```
when I run the script I see it changing with setpci but I see no effect on screen

> **Toz said:**
> Things to try:

1. Kernel parameters
- acpi_backlight=vendor
- acpi_osi=
- acpi_osi=\"Linux\"

I tried those however you didn't specify if you're supposed to try them together, I've tried separately appending to the linux line. Also I tried acpi_backlight=dell
now I rebooted normally however I see  /sys/class/backlight/acpi_video0/ instead of /sys/class/backlight/dell_backlight/

I tried older kernel version but it boot's in low graphic mode, I think it's doesn't work because you suppose to reinstall the ATI driver again compiling for the current kernel.

What do you suggest?
thanks!

---

### Post by iRide113 on 2011-07-08
> **Toz said:**
> 
```
setpci -s 00:02.0 F4.B=77
```

Nothing comes up.

> **Toz said:**
> 
```
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness
```

I get:
```
bash: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
```

________________________________________________

> **Toz said:**
> 
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight 
sudo apt-get update
```

Return:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 77C69C59057A766866EE16C7E0319082F37F3AB0
gpg: requesting key F37F3AB0 from hkp server keyserver.ubuntu.com

gpg: key F37F3AB0: "Launchpad fixes for aprsd" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@Tony-Inspiron17R-Ubuntu:/home/tony# sudo apt-get update
Ign http://mirror.hmc.edu natty InRelease
Ign http://mirror.hmc.edu natty-updates InRelease                              
Ign http://mirror.hmc.edu natty-security InRelease                             
Ign http://mirror.hmc.edu natty-proposed InRelease                             
Hit http://mirror.hmc.edu natty Release.gpg                                    
Hit http://mirror.hmc.edu natty-updates Release.gpg                            
Hit http://mirror.hmc.edu natty-security Release.gpg                           
Ign http://linux.dropbox.com natty InRelease                                   
Get:1 http://mirror.hmc.edu natty-proposed Release.gpg [198 B]                 
Hit http://linux.dropbox.com natty Release.gpg                                 
Hit http://mirror.hmc.edu natty Release                                        
Hit http://mirror.hmc.edu natty-updates Release                                
Hit http://mirror.hmc.edu natty-security Release                               
Hit http://linux.dropbox.com natty Release                                     
Get:2 http://mirror.hmc.edu natty-proposed Release [30.0 kB]                   
Hit http://linux.dropbox.com natty/main amd64 Packages                         
Ign http://linux.dropbox.com natty/main TranslationIndex                       
Ign http://download.tuxfamily.org natty InRelease                              
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://ppa.launchpad.net natty InRelease                                   
Get:3 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://mirror.hmc.edu natty/main Sources                                   
Hit http://mirror.hmc.edu natty/restricted Sources                             
Hit http://mirror.hmc.edu natty/universe Sources                               
Hit http://mirror.hmc.edu natty/multiverse Sources                             
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://mirror.hmc.edu natty/main amd64 Packages                            
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com natty Release                                 
Hit http://mirror.hmc.edu natty/restricted amd64 Packages                      
Ign http://linux.dropbox.com natty/main Translation-en_US                      
Hit http://mirror.hmc.edu natty/universe amd64 Packages                        
Hit http://mirror.hmc.edu natty/multiverse amd64 Packages                      
Ign http://linux.dropbox.com natty/main Translation-en                         
Ign http://mirror.hmc.edu natty/main TranslationIndex                          
Ign http://mirror.hmc.edu natty/multiverse TranslationIndex                    
Get:4 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Ign http://mirror.hmc.edu natty/restricted TranslationIndex                    
Ign http://mirror.hmc.edu natty/universe TranslationIndex                      
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://mirror.hmc.edu natty-updates/main Sources                           
Hit http://mirror.hmc.edu natty-updates/restricted Sources                     
Hit http://mirror.hmc.edu natty-updates/universe Sources                       
Hit http://mirror.hmc.edu natty-updates/multiverse Sources                     
Hit http://mirror.hmc.edu natty-updates/main amd64 Packages                    
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://mirror.hmc.edu natty-updates/restricted amd64 Packages              
Hit http://mirror.hmc.edu natty-updates/universe amd64 Packages                
Hit http://mirror.hmc.edu natty-updates/multiverse amd64 Packages              
Ign http://mirror.hmc.edu natty-updates/main TranslationIndex                  
Get:5 http://ppa.launchpad.net natty Release [9,770 B]                         
Ign http://mirror.hmc.edu natty-updates/multiverse TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/restricted TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/universe TranslationIndex              
Hit http://mirror.hmc.edu natty-security/main Sources                          
Hit http://mirror.hmc.edu natty-security/restricted Sources                    
Hit http://mirror.hmc.edu natty-security/universe Sources                      
Hit http://mirror.hmc.edu natty-security/multiverse Sources                    
Hit http://mirror.hmc.edu natty-security/main amd64 Packages                   
Hit http://mirror.hmc.edu natty-security/restricted amd64 Packages             
Hit http://mirror.hmc.edu natty-security/universe amd64 Packages               
Hit http://mirror.hmc.edu natty-security/multiverse amd64 Packages             
Ign http://mirror.hmc.edu natty-security/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-security/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-security/restricted TranslationIndex           
Ign http://mirror.hmc.edu natty-security/universe TranslationIndex             
Get:6 http://mirror.hmc.edu natty-proposed/restricted amd64 Packages [14 B]    
Hit http://ppa.launchpad.net natty Release                                     
Get:7 http://mirror.hmc.edu natty-proposed/main amd64 Packages [138 kB]        
Get:8 http://ppa.launchpad.net natty/main Sources [2,382 B]                    
Get:9 http://ppa.launchpad.net natty/main amd64 Packages [5,664 B]             
Get:10 http://download.tuxfamily.org natty Release.gpg [198 B]                 
Hit http://extras.ubuntu.com natty/main Sources                                
Get:11 http://download.tuxfamily.org natty Release [2,844 B]                   
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:12 http://download.tuxfamily.org natty/cairo-dock amd64 Packages [3,157 B] 
Get:13 http://mirror.hmc.edu natty-proposed/multiverse amd64 Packages [1,300 B]
Get:14 http://mirror.hmc.edu natty-proposed/universe amd64 Packages [20.7 kB]  
Ign http://download.tuxfamily.org natty/cairo-dock TranslationIndex            
Ign http://mirror.hmc.edu natty-proposed/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-proposed/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-proposed/restricted TranslationIndex 
Ign http://mirror.hmc.edu natty-proposed/universe TranslationIndex   
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://download.tuxfamily.org natty/cairo-dock Translation-en_US           
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://download.tuxfamily.org natty/cairo-dock Translation-en              
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://mirror.hmc.edu natty/main Translation-en_US                         
Ign http://mirror.hmc.edu natty/main Translation-en                            
Ign http://mirror.hmc.edu natty/multiverse Translation-en_US                   
Ign http://mirror.hmc.edu natty/multiverse Translation-en                      
Ign http://mirror.hmc.edu natty/restricted Translation-en_US                   
Ign http://mirror.hmc.edu natty/restricted Translation-en                      
Ign http://mirror.hmc.edu natty/universe Translation-en_US                     
Ign http://mirror.hmc.edu natty/universe Translation-en                        
Ign http://mirror.hmc.edu natty-updates/main Translation-en_US                 
Ign http://mirror.hmc.edu natty-updates/main Translation-en                    
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en              
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en              
Ign http://mirror.hmc.edu natty-updates/universe Translation-en_US             
Ign http://mirror.hmc.edu natty-updates/universe Translation-en                
Ign http://mirror.hmc.edu natty-security/main Translation-en_US                
Ign http://mirror.hmc.edu natty-security/main Translation-en                   
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en_US          
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en             
Ign http://mirror.hmc.edu natty-security/restricted Translation-en_US          
Ign http://mirror.hmc.edu natty-security/restricted Translation-en             
Ign http://mirror.hmc.edu natty-security/universe Translation-en_US            
Ign http://mirror.hmc.edu natty-security/universe Translation-en               
Ign http://mirror.hmc.edu natty-proposed/main Translation-en_US                
Ign http://mirror.hmc.edu natty-proposed/main Translation-en                   
Ign http://mirror.hmc.edu natty-proposed/multiverse Translation-en_US          
Ign http://mirror.hmc.edu natty-proposed/multiverse Translation-en             
Ign http://mirror.hmc.edu natty-proposed/restricted Translation-en_US          
Ign http://mirror.hmc.edu natty-proposed/restricted Translation-en             
Ign http://mirror.hmc.edu natty-proposed/universe Translation-en_US            
Ign http://mirror.hmc.edu natty-proposed/universe Translation-en               
Fetched 214 kB in 12s (17.8 kB/s)                                              
Reading package lists... Done
root@Tony-Inspiron17R-Ubuntu:/home/tony# sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 77C69C59057A766866EE16C7E0319082F37F3AB0
gpg: requesting key F37F3AB0 from hkp server keyserver.ubuntu.com
gpg: key F37F3AB0: "Launchpad fixes for aprsd" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@Tony-Inspiron17R-Ubuntu:/home/tony# sudo apt-get update
Ign http://mirror.hmc.edu natty InRelease
Ign http://mirror.hmc.edu natty-updates InRelease                              
Ign http://mirror.hmc.edu natty-security InRelease                             
Ign http://mirror.hmc.edu natty-proposed InRelease                             
Hit http://mirror.hmc.edu natty Release.gpg                                    
Ign http://linux.dropbox.com natty InRelease                                   
Hit http://mirror.hmc.edu natty-updates Release.gpg                            
Hit http://mirror.hmc.edu natty-security Release.gpg                           
Hit http://mirror.hmc.edu natty-proposed Release.gpg                           
Hit http://linux.dropbox.com natty Release.gpg                                 
Hit http://mirror.hmc.edu natty Release                                        
Hit http://mirror.hmc.edu natty-updates Release                                
Hit http://mirror.hmc.edu natty-security Release                               
Hit http://linux.dropbox.com natty Release                                     
Hit http://mirror.hmc.edu natty-proposed Release                               
Hit http://mirror.hmc.edu natty/main Sources                                   
Hit http://mirror.hmc.edu natty/restricted Sources                             
Hit http://mirror.hmc.edu natty/universe Sources                               
Hit http://mirror.hmc.edu natty/multiverse Sources                             
Hit http://mirror.hmc.edu natty/main amd64 Packages                            
Hit http://mirror.hmc.edu natty/restricted amd64 Packages                      
Hit http://mirror.hmc.edu natty/universe amd64 Packages                        
Hit http://mirror.hmc.edu natty/multiverse amd64 Packages                      
Ign http://mirror.hmc.edu natty/main TranslationIndex                          
Ign http://mirror.hmc.edu natty/multiverse TranslationIndex                    
Ign http://mirror.hmc.edu natty/restricted TranslationIndex                    
Ign http://mirror.hmc.edu natty/universe TranslationIndex                      
Hit http://mirror.hmc.edu natty-updates/main Sources                           
Hit http://mirror.hmc.edu natty-updates/restricted Sources                     
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://linux.dropbox.com natty/main amd64 Packages                         
Ign http://download.tuxfamily.org natty InRelease                              
Ign http://archive.canonical.com natty InRelease                               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://mirror.hmc.edu natty-updates/universe Sources                       
Hit http://mirror.hmc.edu natty-updates/multiverse Sources                     
Hit http://mirror.hmc.edu natty-updates/main amd64 Packages                    
Hit http://mirror.hmc.edu natty-updates/restricted amd64 Packages              
Hit http://mirror.hmc.edu natty-updates/universe amd64 Packages                
Hit http://mirror.hmc.edu natty-updates/multiverse amd64 Packages              
Ign http://mirror.hmc.edu natty-updates/main TranslationIndex                  
Ign http://mirror.hmc.edu natty-updates/multiverse TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/restricted TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/universe TranslationIndex              
Ign http://linux.dropbox.com natty/main TranslationIndex                       
Hit http://mirror.hmc.edu natty-security/main Sources                          
Hit http://mirror.hmc.edu natty-security/restricted Sources                    
Hit http://mirror.hmc.edu natty-security/universe Sources                      
Hit http://mirror.hmc.edu natty-security/multiverse Sources                    
Hit http://mirror.hmc.edu natty-security/main amd64 Packages                   
Hit http://mirror.hmc.edu natty-security/restricted amd64 Packages             
Hit http://mirror.hmc.edu natty-security/universe amd64 Packages               
Hit http://mirror.hmc.edu natty-security/multiverse amd64 Packages             
Ign http://mirror.hmc.edu natty-security/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-security/multiverse TranslationIndex           
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:1 http://download.tuxfamily.org natty Release.gpg [198 B]                  
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://mirror.hmc.edu natty-security/restricted TranslationIndex           
Ign http://mirror.hmc.edu natty-security/universe TranslationIndex             
Hit http://mirror.hmc.edu natty-proposed/restricted amd64 Packages             
Hit http://mirror.hmc.edu natty-proposed/main amd64 Packages                   
Hit http://mirror.hmc.edu natty-proposed/multiverse amd64 Packages             
Hit http://mirror.hmc.edu natty-proposed/universe amd64 Packages               
Ign http://mirror.hmc.edu natty-proposed/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-proposed/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-proposed/restricted TranslationIndex           
Ign http://mirror.hmc.edu natty-proposed/universe TranslationIndex             
Hit http://extras.ubuntu.com natty Release                                     
Get:2 http://download.tuxfamily.org natty Release [2,844 B]                    
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://linux.dropbox.com natty/main Translation-en_US                      
Ign http://linux.dropbox.com natty/main Translation-en                         
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Get:3 http://download.tuxfamily.org natty/cairo-dock amd64 Packages [3,157 B]  
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://download.tuxfamily.org natty/cairo-dock TranslationIndex            
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                                     
Ign http://mirror.hmc.edu natty/main Translation-en_US                                     
Ign http://mirror.hmc.edu natty/main Translation-en                                        
Ign http://mirror.hmc.edu natty/multiverse Translation-en_US                               
Ign http://mirror.hmc.edu natty/multiverse Translation-en                                  
Ign http://mirror.hmc.edu natty/restricted Translation-en_US                               
Ign http://mirror.hmc.edu natty/restricted Translation-en            
Ign http://mirror.hmc.edu natty/universe Translation-en_US                                 
Ign http://mirror.hmc.edu natty/universe Translation-en                                    
Ign http://mirror.hmc.edu natty-updates/main Translation-en_US                             
Ign http://mirror.hmc.edu natty-updates/main Translation-en                                
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en_US                       
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en                          
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en_US 
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en                          
Ign http://mirror.hmc.edu natty-updates/universe Translation-en_US                         
Ign http://mirror.hmc.edu natty-updates/universe Translation-en      
Ign http://mirror.hmc.edu natty-security/main Translation-en_US                            
Ign http://mirror.hmc.edu natty-security/main Translation-en                               
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en_US
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en   
Ign http://mirror.hmc.edu natty-security/restricted Translation-en_US
Ign http://mirror.hmc.edu natty-security/restricted Translation-en   
Ign http://mirror.hmc.edu natty-security/universe Translation-en_US  
Ign http://mirror.hmc.edu natty-security/universe Translation-en     
Ign http://mirror.hmc.edu natty-proposed/main Translation-en_US      
Ign http://mirror.hmc.edu natty-proposed/main Translation-en         
Ign http://mirror.hmc.edu natty-proposed/multiverse Translation-en_US
Ign http://mirror.hmc.edu natty-proposed/multiverse Translation-en   
Ign http://mirror.hmc.edu natty-proposed/restricted Translation-en_US                      
Ign http://mirror.hmc.edu natty-proposed/restricted Translation-en                         
Ign http://mirror.hmc.edu natty-proposed/universe Translation-en_US                        
Ign http://mirror.hmc.edu natty-proposed/universe Translation-en                           
Ign http://archive.canonical.com natty/partner Translation-en_US                           
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://download.tuxfamily.org natty/cairo-dock Translation-en_US
Ign http://download.tuxfamily.org natty/cairo-dock Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Fetched 6,199 B in 4s (1,269 B/s)
Reading package lists... Done

```

Will restart and see if anything happened.

**EDIT**: Still nothing after restart...

---

### Post by Toz on 2011-07-09
Did you update the system? You should have new updates to install. 
```
sudo apt-get upgrade
```

Post back the results.

---

### Post by iRide113 on 2011-07-11
> **Toz said:**
> Did you update the system? You should have new updates to install. 
```
sudo apt-get upgrade
```

Post back the results.

Sorry Ubuntu hasn't been working the last few days. You can check out the thread [here]("http://ubuntuforums.org/showthread.php?t=1801461"). And before it stopped working, I did update and still nothing happened.

---

