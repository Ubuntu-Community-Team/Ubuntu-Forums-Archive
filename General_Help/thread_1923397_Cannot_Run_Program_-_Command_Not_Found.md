---
title: "Cannot Run Program - Command Not Found"
date: 2012-02-10
forum: General Help
---

### Post by M1GEO on 2012-02-10
Hi All.

I have a very strange problem and I'm hoping someone will know what I'm missing.  But it has been a very long day...

I have a binary application (serialdump-linux) which is used to get data from Wireless Sensor Nodes.  It doesn't particularly matter.  

It is located here: '/home/george/contiki/tools/sky/serialdump-linux' 

The standard place for it when using Contiki.

I cannot get this program to run.  Any attempt at doing so results in "Command not found" errors from bash.

```
~/contiki/examples/rime$ /home/george/contiki/tools/sky/serialdump-linux
bash: /home/george/contiki/tools/sky/serialdump-linux: No such file or directory

```

The file does exist and is executable:

```
$ ls -larth /home/george/contiki/tools/sky/serialdump-linux
-rwxr-xr-x 1 george george 15K 2012-02-10 18:37 /home/george/contiki/tools/sky/serialdump-linux
```

Even CD'ing into the directory and then running it doesn't get me anywhere:

```
~/contiki/tools/sky$ ./serialdump-linux 
bash: ./serialdump-linux: No such file or directory
```

This works on other computers, 64-bit Ubuntu 10.04.3 LTS.

So essentially, my question is, can you please help me? I'm desperate! Haha.

---

### Post by LewisTM on 2012-02-10
Please post the output of the [FONT="Courier New"]mount[/FONT] command.

I'm looking specifically at a noexec parameter that might have slipped in your filesystems and would override the executable bit.

Once I had to explicitly put an extra 'exec' fstab parameter for my new XFS home partition in order to run programs. I think I was running 10.04 at the time.

Cheers!

---

### Post by M1GEO on 2012-02-10
As you will guess from the filesystems, it's a Macbook. Not that I expect this should make any difference.  As requested, the output of mount:

```
george@georgesmart-mac:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/george/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=george)
/dev/sda3 on /media/Recovery HD type hfsplus (rw,nosuid,nodev,uhelper=udisks)

```

---

### Post by LewisTM on 2012-02-10
That looks right, nothing out of the ordinary.
How about putting sudo in front of the script command?
That would tell us if it's a permission problem.

---

### Post by Khayyam on 2012-02-10
> **Compu-king said:**
>  [...] This works on other computers, 64-bit Ubuntu 10.04.3 LTS.

Does that mean you have a 64bit, or it works on 64bit? .. its hard to tell from the above.

Does the output of 'file serialdump-linux' show it to be a 'ELF 32bit LSB'?

What does the output of 'ldd serialdump-linux' show?

If you have a 64bit processor, don't have ia32-libs installed, and didn't compile this yourself, then I imagine 'serialdump-linux' was compiled for 32bit, and so you'll need ia32-libs (and perhaps other libraries) to run it. 

```
apt-get install ia32-libs
```

If they provide source code then you should compile it for 64bit (my guess though, from the name, is that this isn't open source/free software).

HTH ...

---

### Post by M1GEO on 2012-02-10
Firstly it's a proper program (as in, not a script).  I tried 'sudo' in front of it, and it come up with something very similar. I don't remember exactly what (it's at work now, I'm at home).

> Does that mean you have a 64bit, or it works on 64bit? .. its hard to tell from the above.

Sorry, I should have made this clearer. This is on a 64bit version of Ubuntu. I've had this exact program running on 64bit Ubuntu versions (10.04 through 11.10).

> Does the output of 'file serialdump-linux' show it to be a 'ELF 32bit LSB'?

Yes.

```
serialdump-linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, not stripped
```

What does the output of 'ldd serialdump-linux' show?

```
ldd serialdump-linux
        linux-gate.so.1 =>  (0xf772d000)
        libc.so.6 => /lib32/libc.so.6 (0xf75b4000)
        /lib/ld-linux.so.2 (0xf772e000)
```

That had completely slipped my mind. To be honest, I had completely forgotten about *ldd*!

> If you have a 64bit processor, don't have ia32-libs installed, and didn't compile this yourself, then I imagine 'serialdump-linux' was compiled for 32bit, and so you'll need ia32-libs (and perhaps other libraries) to run it.

I have a 64bit CPU & OS, I don't have ia32-libs installed (probably my problem) and I didn't compile it myself (it comes with Contiki prebuilt).  I will check that out on Monday when I'm back in the office, and update this thread - hopefully marking it solved.

I agree this is probably the likely cause of it. Just seems a strange response from BASH to deny being able to find the binary executable.

Thanks for all your help thus far! :)

---

### Post by Khayyam on 2012-02-10
> **Compu-king said:**
> [...] I agree this is probably the likely cause of it. Just seems a strange response from BASH to deny being able to find the binary executable.

I thought this when first encountering a similar problem, but on reflection now think its quite logical. It is not as if bash checks to see what the file is, it just trys to execute it, and as its non-executable (32bit on 64bit architecture) its much the same as passing a non-existant command. The error "Command not found" is about all bash can say about the situation as there is no "executable" 'serialdump-linux'.

> **Compu-king said:**
> Thanks for all your help thus far!

Your welcome .. installing ia32-libs should solve the problem as the libraries it links to are from glibc.

best ...

---

### Post by M1GEO on 2012-02-13
Just to let you know that this fixed the issue.

```
george@georgesmart-mac:~/contiki/tools/sky$ ./serialdump-linux -b115200 /dev/ttyS0
connecting to /dev/ttyS0 (115200) [OK]
```

Thanks very much for all you're help :)

---

