---
title: "How to trace this bug?"
date: 2009-10-06
forum: General Help
---

### Post by g.a. on 2009-10-06
Hi all,

I have a problem with the shut down.

Sometimes (I'm not able to reproduce it) the shut down procedure hangs permanently. The only solution is an hard switch off.

What is annoying is that I do not have enough information to clearly describe the problem because the screen is frozen and, at the successive turn on, I'm not able to find any log message associated to the problem.

I can only describe you my frozen screen. 

It is full of messages and (yes, I copied by hand) the last 3 lines contain
```
[32609.00] RIP [<ffffffff806999cc>] thread_return + 0x97/0x36b
[32609.00]  RSP <ffff880116033b50>
[32610.00] -- [ end trace 68d4b5e33ad0f556 ] ---
```

(to be precise I know that the numbers in the first square bracket is the time from the turn on so I did not copied).

I know it is a quite hermetic description but any help is appreciated. This bug occurs since almost 9 months, with all the kernels properly updated and both kubuntu and ubuntu distributions.

Thanks,
g.

---

### Post by Giblet5 on 2009-10-06
The next time it happens, immediately boot back up and save the next-to-last syslog file. The problem is probably documented right at the end of that log file.

They're kept in /var/log.

Do an ```
ls -ltr /var/log/syslog*
``` to identify the correct log file to save.

---

### Post by g.a. on 2009-10-06
I have already searched in the directory /var/log

almost all the files both by visual inspection and using grep and zgrep commands

concerning the syslog this is what is saved in correspondence to my problem:

```
Oct  6 17:37:59 trinity init: tty4 main process (2524) killed by TERM signal                                                                         
Oct  6 17:37:59 trinity init: tty5 main process (2525) killed by TERM signal                                                                         
Oct  6 17:37:59 trinity init: tty2 main process (2530) killed by TERM signal                                                                         
Oct  6 17:37:59 trinity init: tty3 main process (2531) killed by TERM signal                                                                         
Oct  6 17:37:59 trinity init: tty6 main process (2532) killed by TERM signal                                                                         
Oct  6 17:37:59 trinity init: tty1 main process (3391) killed by TERM signal                                                                         
Oct  6 17:38:00 trinity bonobo-activation-server (gianluca-8289): could not associate with desktop session: Failed to connect to socket /tmp/dbus-PC1TzSkvi9:
 Connection refused                                                                                                                                          
Oct  6 17:38:05 trinity bluetoothd[3023]: Unregistered interface org.bluez.NetworkPeer on path /org/bluez/3023/hci0                                          
Oct  6 17:38:05 trinity bluetoothd[3023]: Unregistered interface org.bluez.NetworkHub on path /org/bluez/3023/hci0                                           
Oct  6 17:38:05 trinity bluetoothd[3023]: Unregistered interface org.bluez.NetworkRouter on path /org/bluez/3023/hci0                                        
Oct  6 17:38:06 trinity bluetoothd[3023]: bridge pan0 removed                                                                                                
Oct  6 17:38:06 trinity bluetoothd[3023]: Stopping SDP server                                                                                                
Oct  6 17:38:06 trinity bluetoothd[3023]: Exit                                                                                                               
Oct  6 17:38:06 trinity exiting on signal 15    
```

someone told me that probably the system did not have the time to save the bug.

thanks for you reply
g.

---

### Post by ibuclaw on 2009-10-06
thread_return appears to be an asm function in the system part of the Linux kernel.

That comes under: arch/x86/include/asm/system.h
It is called from a define named 'switch_to'
To whom's job appears to be to "*Save restore flags to clear handle leaking NT*", as described in the comment directly above it.
In another comment, it says "*Saving eflags is important. It switches not only IOPL between tasks, it also protects other tasks from NT leaking through sysenter etc.*"

And this is what the Documentation has to say:
> 
Context switch
==============
1. Runqueue locking
By default, the switch_to arch function is called with the runqueue
locked. This is usually not a problem unless switch_to may need to
take the runqueue lock. This is usually due to a wake up operation in
the context switch. See arch/ia64/include/asm/system.h for an example.

To request the scheduler call switch_to with the runqueue unlocked,
you must `#define __ARCH_WANT_UNLOCKED_CTXSW` in a header file
(typically the one where switch_to is defined).

Unlocked context switches introduce only a very minor performance
penalty to the core scheduler implementation in the CONFIG_SMP case.

2. Interrupt status
By default, the switch_to arch function is called with interrupts
disabled. Interrupts may be enabled over the call if it is likely to
introduce a significant interrupt latency by adding the line
`#define __ARCH_WANT_INTERRUPTS_ON_CTXSW` in the same place as for
unlocked context switches. This define also implies
`__ARCH_WANT_UNLOCKED_CTXSW`. See arch/arm/include/asm/system.h for an
example.


OK, maybe a deadend... lets just look at your output again:
```
[32609.00] RIP [<ffffffff806999cc>] thread_return + 0x97/0x36b
[32609.00]  RSP <ffff880116033b50>
[32610.00] -- [ end trace 68d4b5e33ad0f556 ] ---
```

The job of **RIP** is important, this will help us pinpoint exactly which instruction that caused the warning.

run:
```
grep "CONFIG_DEBUG_INFO" /boot/config*
```
If that outputs:
> **CONFIG_DEBUG_INFO=y**
on the kernel you are booted on, you are in luck. :)

Okies, first you have to decompress your kernel.
Easier said than done.

First, we have to find the GZ signature in the kernel, which is '**1f 8b 08 00**'
```
od -A d -t x1 /boot/vmlinuz-$(uname -r) | grep '1f 8b 08 00' --colour
```
And you'll get an output like this:
> 0014432 f3 a5 fc 5e 8d 83 20 6d 3a 00 ff e0 [COLOR="Red"]1f 8b 08 00[/COLOR]
Now, two things are important here:
[LIST=1]
[*]The First number outputted (in my example, it's **0014432**).
[*]The number of octal values before the signature (in my example, we have **12**).
[/LIST]
Now, simple maths, 14432 + 12 = **14444**

Next, we dd out the gzip file and extract it to the executable kernel to the filename **vmlinux**
```
dd if=/boot/vmlinuz-$(uname -r) bs=1 skip=**14444** | zcat > vmlinux
```
If all went fine, you should see this:
```

$ file vmlinux 
vmlinux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped

```

Now we can debug. :D
```
addr2line -e vmlinux -i ffffffff806999cc
```
The 'ffffffff806999cc' is the instruction of the vmlinux file that gave the RIP error, if that worked, then you should see a list of files and their line numbers outputted.

If not, there is another thing we can do:
```
objdump -d --no-show-raw-insn vmlinux | grep -C 8 ffffffff806999cc:
```
Which will print out the asm of the instruction and what happened 8 instructions prior and after.

If that doesn't produce anything else of importance, only thing I can really suggest is either looking in the logs, or recompiling the kernel with better debugging.

Can't really say much else, other than please post any output that you find.

Regards
Iain

---

### Post by g.a. on 2009-10-07
thanks a lot for your reply.

well, the start is promising:

```

grep "CONFIG_DEBUG_INFO" /boot/config*
/boot/config-2.6.27-14-generic:CONFIG_DEBUG_INFO=y
/boot/config-2.6.28-13-generic:CONFIG_DEBUG_INFO=y
/boot/config-2.6.28-14-generic:CONFIG_DEBUG_INFO=y
/boot/config-2.6.28-15-generic:CONFIG_DEBUG_INFO=y

```

now

```
od -A d -t x1 /boot/vmlinuz-$(uname -r) | grep '1f 8b 08 00' --colour
0013440 8d 83 d0 3a 35 00 ff e0 36 38 35 00 1f 8b 08 00
```

so I have to add the first number with the number of couples following it and before the signature that gives me

```
13440+12 = 13452
```

then

```
dd if=/boot/vmlinuz-$(uname -r) bs=1 skip=13452 | zcat > vmlinux

gzip: stdin: decompression OK, trailing garbage ignored
3500180+0 records in
3500180+0 records out
3500180 bytes (3.5 MB) copied, 10.7264 s, 326 kB/s
```

and 
```

file vmlinux
vmlinux: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, stripped
```

unfortunately

```
addr2line -e vmlinux -i ffffffff806999cc
??:0
```

and finally

```
objdump -d --no-show-raw-insn vmlinux | grep -C 8 ffffffff806999cc:
ffffffff806999b8:       jne    0xffffffff80699514
ffffffff806999be:       add    $0x78,%rsp
ffffffff806999c2:       pop    %rbx
ffffffff806999c3:       pop    %r12
ffffffff806999c5:       pop    %r13
ffffffff806999c7:       pop    %r14
ffffffff806999c9:       pop    %r15
ffffffff806999cb:       leaveq
ffffffff806999cc:       retq
ffffffff806999cd:       nopl   (%rax)
ffffffff806999d0:       mov    -0x60(%rbp),%rcx
ffffffff806999d4:       cmpq   $0x0,0x218(%rcx)
ffffffff806999dc:       jne    0xffffffff80699754
ffffffff806999e2:       mov    -0x60(%rbp),%rsi
ffffffff806999e6:       mov    0x8(%rsi),%rax
ffffffff806999ea:       mov    0x1c(%rax),%edx
ffffffff806999ed:       mov    0x3148cc(%rip),%rax        # 0xffffffff809ae2c0

```

is there any usefull information here? I'm not able to find it...

thanks,
g.

---

### Post by ibuclaw on 2009-10-07
> **g.a. said:**
> thanks a lot for your reply.

well, the start is promising:


Hmm... looks like the human readable bits were removed before the the vmlinux file was gzipped, so no, unfortunately not.

The only other thing you can do then is compile the vmlinux executable yourself, and run off it.

Steps are:
```

sudo -s
apt-get install linux-source
cd /usr/src
tar -xvf linux-source-2.6.28.tar.bz2
cd linux-source-2.6.28
cp /boot/config-$(uname -r) .config
yes "" | make oldconfig
make bzImage
exit

```
This will now compile a kernel executable image based on the exact configuration that you already use in Ubuntu.

Next thing to do is backup the original.
```
sudo rename 's/$/.old/' /boot/vmlinuz-$(uname -r)
```
Copy in the new one:
```
sudo cp arch/x86/boot/bzImage /boot/vmlinuz-$(uname -r)
```
And backup the vmlinux executable for debugging reference.
```

mkdir ~/kernel
cp vmlinux ~/kernel

```

Then reboot, and wait for the failure to happen again.
When it does, write down **everything** that you see, even if you have to take screenshots.

Then undergo the same process with the 'addr2line' and the 'objdump' commands and the memory address in the 'RIP' lines. (make a note of other lines too, in the exact order, as that will help debug the issue).
```

addr2line -e **~/kernel/vmlinux** -i <instruction address>
objdump -d --no-show-raw-insn **~/kernel/vmlinux** | grep -C 8 <instruction address>:

```
With that info, and some general hardware information should be enough to report at least a bug.

But if you report back here, what I'll do is subscribe to this thread and advise you of which route to take, and maybe even try to identify which module/built-in is causing the issue.

Regards
Iain

Also, you can safely remove any previous kernels:
```
sudo aptitude purge linux-image-2.6.28-13-generic linux-image-2.6.28-14-generic
```

---

### Post by g.a. on 2009-10-12
dear tinivole,

I'm sorry for the late reply.

for other reasons I had to make a fresh ubuntu 9.04 installation.

4 days without bugs... :)

the former installation was a kubuntu 9.04 with an ubuntu-desktop on top of it.

let wait for the bug again...

thanks for your help
g.

---

