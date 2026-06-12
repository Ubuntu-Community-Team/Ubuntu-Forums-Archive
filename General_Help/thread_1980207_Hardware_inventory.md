---
title: "Hardware inventory"
date: 2012-05-14
forum: General Help
---

### Post by bilijoe on 2012-05-14
Is there a way to get Ubuntu to give you a list of the hardware in your system, and some details about it. E.g., your processor brand, model, architecture, speed, etc.; manufacturer and model of sound board, video board, etc., installed memory amount, type, speed, etc., etc.? I am looking for something with functionality similar to the 'AIDA' Windoz utility. 'Sysinfo' provides some information, but I am looking for something that gives [lots] more details.):P

---

### Post by roelforg on 2012-05-14
```

whoami
sudo lshw > /home/<output of previous command here>/hw.txt

```
Run it in terminal and wait for your prompt to come back, it may take a while.
There should now be a file named hw.txt in your homedir that contains a lot of hw info (mine is 1000+ lines, is that enough? It'll even tell you about your cpus l* caches to what ram-area your gfx-card has to what the clockspeed of your ram is).

---

### Post by pbrane on 2012-05-14
or
```

sudo lshw $HOME/hw.txt

```

---

### Post by oldfred on 2012-05-15
I have an HTML version of lshw and some more commands.

If using sudo, run any sudo command like ls first. 
Sometimes sudo & redirect have issues.
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

HardInfo is a small application that displays information about your hardware and operating system
hardinfo
system, preferences, system profiler & performance (hardinfo in synaptic)
sysinfo is a graphical tool that is able to display some hardware and software information about the computer it is run on.
sysinfo

sysbench is a useful tool for benchmarking drives. It's in the ubuntu repos.
sudo apt-get install sysbench
sysbench --test=fileio --file-num=64 --file-total-size=$size --init-rng=on --file-extra-flags=direct prepare
sysbench --test=fileio --file-total-size=$size --file-test-mode=$mode --max-time=60 --max-requests=100000000 --num-threads=$threads --init-rng=on --file-num=64 --file-extra-flags=direct --file-fsync-freq=0 --file-block-size=16384 run

---

### Post by bilijoe on 2012-05-15
Thanks!:popcorn::popcorn::popcorn::)

---

### Post by HerixFromParis on 2012-06-23
Thank you so much oldfred.
The trick with [COLOR="Blue"]lshw -html[/COLOR] is pretty neat !

---

