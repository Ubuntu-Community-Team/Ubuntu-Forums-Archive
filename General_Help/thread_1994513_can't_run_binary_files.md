---
title: "can't run binary files"
date: 2012-06-02
forum: General Help
---

### Post by cadcam on 2012-06-02
Hello, I have a file, and terminal won't run it.  I don't understand why.  There are a number of files in directory, but the binaries are the only ones that fail.  help?  I use this program for my work, and without it I'm in a world of un-productivity.  I just did a clean install of 12.04.  Am I missing a vital package?  Why are there no errors, is it the binary itself?


```
mantra@Mantra:~$ cd iambuff/mplab\ 1.2\ full\ package/
mantra@Mantra:~/iambuff/mplab 1.2 full package$ ls
mplabc18-v3.40-linux-full-installer.run  picc-9.83-linux.run
mplabx-ide-v1.20-linux-installer.run     picc-9.83-linux.zip
picc-18-9.80.11162-linux.run             xc8-v1.00-linux.run
PICC_18_9_80_linux_run.zip
mantra@Mantra:~/iambuff/mplab 1.2 full package$ sudo ./mplabx-ide-v1.20-linux-installer.run 
[sudo] password for mantra: 
mantra@Mantra:~/iambuff/mplab 1.2 full package$ sudo ./mplabx-ide-v1.20-linux-installer.run -v
mantra@Mantra:~/iambuff/mplab 1.2 full package$
```

---

### Post by synapsys on 2012-06-02
I'm thinking permissions? Show us a
```
ls -la
```
of that folder...

---

### Post by cadcam on 2012-06-02
```
mantra@Mantra:~/iambuff/mplab 1.2 full package$ ls -la
total 728580
drwx------ 2 mantra mantra      4096 Jun  2 15:33 .
drwx------ 3 mantra mantra      4096 Jun  2 15:09 ..
-rwxr-xr-x 1 mantra mantra  73664889 Jun  1 01:48 mplabc18-v3.40-linux-full-installer.run
-rwxrwxr-x 1 mantra mantra 240717751 Jun  1 01:11 mplabx-ide-v1.20-linux-installer.run
-rwxrwxr-x 1 mantra mantra 128463376 Sep 26  2011 picc-18-9.80.11162-linux.run
-rw-r--r-- 1 mantra mantra 127153146 Jun  1 02:10 PICC_18_9_80_linux_run.zip
-rwxrwxr-x 1 mantra mantra  17345037 Sep 21  2011 picc-9.83-linux.run
-rw-r--r-- 1 mantra mantra  16950192 Jun  1 02:08 picc-9.83-linux.zip
-rwxr-xr-x 1 mantra mantra 141746412 Jun  1 02:04 xc8-v1.00-linux.run
mantra@Mantra:~/iambuff/mplab 1.2 full package$ 

```

---

### Post by forrestcupp on 2012-06-02
Do they really need to be run with a sudo command?

Also, did you make them executable before you tried to run them?
```
chmod +x ./*filename*
```

---

### Post by cadcam on 2012-06-02
```

mantra@Mantra:~/iambuff/mplab 1.2 full package$ ./mplabx-ide-v1.20-linux-installer.run 
mantra@Mantra:~/iambuff/mplab 1.2 full package$ echo $?
127
mantra@Mantra:~/iambuff/mplab 1.2 full package$
```

---

### Post by cadcam on 2012-06-02
I have run them with and without super, and as far as I can see, they are marked as executable.  I'm seriously mystefied.  I've never had a problem installing them before, v1.2 just came out, but other's have had no problem putting 1.2 on pangolin.  It's not just the mplab file itself, the accompanying binaries are also useless right now.  baffling.

Another note, these microchip programs usually run in their own window, not the terminal, which led to me believe that I'm lacking a requirement. I have installed java 6, which is the only requirement as far as I know.

@forestcupp: as far as running them as root, they usually will ask you to reopen them as root if you do not.

---

### Post by devaiah on 2012-06-02
I recently upgraded to Ubuntu 12.04 and even I had a similar problem installing MPLABX IDE v1.20. I even changed the permission to "executable" but in vain, it didn't help... 
SERIOUS HELP REQUIRED!!

---

### Post by cadcam on 2012-06-03
Solution seen hurrrrr:
[http://askubuntu.com/questions/145716/cannot-install-mplab-ide-x-from-the-terminal-silently-exits]("http://askubuntu.com/questions/145716/cannot-install-mplab-ide-x-from-the-terminal-silently-exits")



I believe the solution is that the DAMN thing runs in a 32 environment, EVEN THOUGH MICROCHIP says it runs in 64 as well, program vs installer I suppose.  keep it might up microchip, you might just push us all to atmel.  


Thanks for the help.

---

### Post by synapsys on 2012-06-04
In that case, you should be able to install it using the 32 bit libraries in 64 bit Ubuntu.

Try running this:

```
Sudo apt-get install ia32-libs
```

Then try installing again.

---

