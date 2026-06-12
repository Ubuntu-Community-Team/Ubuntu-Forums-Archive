---
title: "How to write a series of actions to be executed automatically on boot?"
date: 2011-01-01
forum: General Help
---

### Post by 3602 on 2011-01-01
Basically, to save battery (extend battery life) of computer, I use these commands to shut off my dedicated graphics card:
```
cd acpi_call
sudo insmod acpi_call.ko
./test_off.sh
```Now right now I have to do this manually. Is there some way for the system to execute these automatically when the system boots? Thank you very much.

---

### Post by WorMzy on 2011-01-01
Put the script into /usr/local/bin, and edit /etc/rc.local

```
insmod acpi_call.ko
/usr/local/bin/test_off.sh
```

---

### Post by A_M_S on 2011-01-01
You can copy the commands bellow to a plain text file using nano or other editor.

```

#!/bin/bash
cd acpi_call
sudo insmod acpi_call.ko
./test_off.sh

```

Save the file and change it to executable 

```

sudo chmod 777 your_file

```

Add the file to Startup Applications (system->preferences->startup applications)

---

### Post by 3602 on 2011-01-01
Sorry but neither solutions work.
I tried post #3 first, reboot, monitored power consumption which was 16-17 watts. I manually entered the commands and it immediately dropped to 11 watts.
Then I tried #2. I had to use* sudo mv /path/* because regular copy/paste don't work. I then put the two lines above *exit 0* in the rc.local file, saved then rebooted. Consumption is also 16-17 watts.

---

### Post by neovandeen on 2011-01-02
You also can put it in the crontab. This should look like this:

sudo crontab -u root -e

```

@reboot insmod /path/to/acpi_call.ko
@reboot /path/to/test_off.sh


```

---

### Post by 3602 on 2011-01-02
Sorry but the crontab thing didn't work either.
I put the path as* insmod /home/home_folder_name/acpi_call/acpi_call.ko* right?

---

### Post by 3602 on 2011-01-02
Alright. Got it working by writing:
```
#!/bin/bash
insmod /home/home_folder/acpi_call/acpi_call.ko
./home/home_folder/acpi_call/test_off.sh
```
and saved to *file.sh* (Made it into a script).
Then followed: [http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)
And grepping returned positive. Although Power Management shows 3:30 left, it's already better than 2:00 when the card is on. Gateway says this battery can last 6 hours. Oh well.

---

