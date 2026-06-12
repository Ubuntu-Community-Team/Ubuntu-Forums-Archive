---
title: "2 Mac OSX entries in Grub2"
date: 2010-08-10
forum: General Help
---

### Post by Jack3500 on 2010-08-10
[SIZE=3]There are 2 osx entries in the grub menu one is 32-bit and the other is 64-bit, can someone please tell me how i can get rid of the 32-bit one?
i am using ubuntu 10.4 and snow leopard 10.6.3 

thanks[/SIZE]

---

### Post by Quackers on 2010-08-10
I have the same thing. In mine though 64 bit won't boot any more. Have you checked that both boot?

---

### Post by Jack3500 on 2010-08-10
yes both work correctly, 64 bit boots 64 bit, and 32 bit boots 32 bit

but i only need the 64 bit option

---

### Post by Quackers on 2010-08-10
Ok. Maybe I installed a 32 bit only kext by mistake.
There is a way to make a custom Grub2 menu but I'm afraid I can't find the link. Try the search forum for "custom menu" and I think it will appear. I don't think there is a way to just remove the entry. Maybe somebody more knowledgable than me could confirm/deny that.

---

### Post by Jack3500 on 2010-08-10
Im gonna start playing around with the code, maybe ill replace it with different code from the Internet and see if i get anywhere

---

### Post by drs305 on 2010-08-10
[COLOR="DarkRed"]Edited: The OP, Jack3500, found the solution on his own and recorded it in Post #16. You can read the intervening posts if you wish but going to Post #16 will save you time and effort![/COLOR]

Are they on different partitions? If so, you can add a line to /etc/grub.d/30_os-prober to hide the specific partition. The lines to add would be:
> 
if [ "${DEVICE}" = "/dev/sd[COLOR="Red"]XY[/COLOR]" ]; then
continue
fi


Now the disclaimer: I haven't tried editing 30_os-prober, but I think you could insert it around line 134 so it looked like this. **Change sd[COLOR="Red"]XY[/COLOR] to the appropriate device/partition designation, such as "sd[COLOR="Red"]c5[/COLOR]".**
> for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

[B]# Added to exclude sd[COLOR="Red"]XY[/COLOR]
if [ "${DEVICE}" = "/dev/sd[COLOR="Red"]XY[/COLOR]" ]; then
continue
fi
# End Add[/B]

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

Update grub, and then check the contents of grub.cfg or run the following command to see if the correct menuentry was removed:
```
cat /boot/grub/grub.cfg | grep "menuentry"
```

This is a modification of Section 5 of the Grub 2 Title Tweaks thread linked below.

**Added:** This is listed in the Windows section of the Title Tweaks. If it also works as above for OSX, please post so I can go to that thread and expand it to indicate it also  works in for OSX in the same part of 30_os-prober.

---

### Post by Jack3500 on 2010-08-10
they are both one operating system on one partition, the 32-bit menu entry just boots the os in 32-bit mode

---

### Post by Quackers on 2010-08-10
On mine they are on the same partition (/dev/sda3) but I can live with the extra menu entry. Thanks for the info though :-)

---

### Post by drs305 on 2010-08-10
> **Jack3500 said:**
> they are both one operating system on one partition, the 32-bit menu entry just boots the os in 32-bit mode

EDITED: After reviewing the RESULTS.txt from another thread:
Ok.  Originally I thought you could use the LONGNAME but upon seeing your RESULTS text the $LONGNAME is the same for both OSX entries. 

Since we can't use the LONGNAME variable, perhaps we can do the same thing by using the variable that defines 32-bit or 64-bit.I'll try to come up with how the 32-bit/64-bit variable is set and come up with an answer in a later post.

Again the disclaimer I can't test this as I normally would since I don't have OSX.

---

### Post by Quackers on 2010-08-10
This would be in etc/grub.d not etc/grub  would it?

---

### Post by drs305 on 2010-08-10
> **Quackers said:**
> This would be in etc/grub.d not etc/grub  would it?
Yes. I'll go proof what I typed. The file to edit is /etc/grub.d/30_os-prober.

---

### Post by Quackers on 2010-08-10
Ok, thanks. I'll go and look at it :-)

---

### Post by Quackers on 2010-08-10
The OS X entries for 32 bit and 64 bit don't appear in plain text until line 213 and after of etc/grub.d

```
  macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      cat << EOF
```

Although line 134 looks like what you posted it doesn't actually give the same details

```

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
```

---

### Post by drs305 on 2010-08-10
Quackers,

I believe the entire section beginning around line 134 is all related to finding the other OS's on the system. The first quote you posted is a subset of the entire section. 

Edited: After reviewing the RESULTS.txt from another post:
We'll try placing the *bit* variable conditional after the following once I can come up with it. I'll post back here with the conditional to use: 
>  BOOT="`echo ${OS} | cut -d ':' -f 4`"


You can try it, update grub and then check the /boot/grub/grub.cfg entry to see if it worked correctly *before* you attempt to reboot. If it doesn't, you can remove the conditional section you added, save the file and update grub to return to the original (or just make a backup of 30_os-prober in another directory first).

And of course there is always the custom menu option, which is pretty foolproof and usually much easier.  ;-)

---

### Post by Quackers on 2010-08-10
Yes, the custom menu is another option :-)
I like fiddling though :-) but as it's 3am here it's probably not the time to be making decisions!
The thread is bookmarked for daytime consideration :-)
I bet you're sorry you started now :-)
Apologies to the OP if I've hijacked his thread.

---

### Post by Jack3500 on 2010-08-11
[SIZE=2][SIZE=4]Fixed it !!! :D[/SIZE]

[SIZE=2]All I did was remove this line of code: ```
 osx_entry xnu_kernel 32 
``` from the 30_os-prober file, the line is near the end of the file ( Line 218 for me)[/SIZE][/SIZE][SIZE=2]

[/SIZE][SIZE=2]now it only shows the 64-bit option in the menu


EDIT: wow i think you guys already found that out, i didn't even look at the last couple of posts
[/SIZE]

---

### Post by drs305 on 2010-08-11
> **Jack3500 said:**
> [SIZE=2][SIZE=4]Fixed it !!! :D[/SIZE]

[SIZE=2]All I did was remove this line of code: ```
 osx_entry xnu_kernel 32 
``` from the 30_os-prober file, the line is near the end of the file ( Line 218 for me)[/SIZE][/SIZE][SIZE=2]

[/SIZE][SIZE=2]now it only shows the 64-bit option in the menu


EDIT: wow i think you guys already found that out, i didn't even look at the last couple of posts
[/SIZE]

Glad you found a solution!  Actually, I was still working on another approach by identifying the 32-bit pararmeter; just removing it is even easier.  :-)

Would you please mark the thread SOLVED via the "Thread Tools" at the top right of the original post? Also, apologies that *Quackers* and I partly hijacked the thread.

I intend on including this in my Title Tweaks thread, as apparently your situation isn't unique. Getting rid of the second OSX entry is simple and I thank you for discovering the method to do so.

---

### Post by Jack3500 on 2010-08-11
> I intend on including this in my Title Tweaks thread

By the way thanks for making those threads, basically everything i learned about grub was from that one and a couple of your other threads

---

### Post by drs305 on 2010-08-11
> **Jack3500 said:**
> basically everything i learned about grub was from that one and a couple of your other threads

That explains why you had to figure it out for yourself!  :lolflag:

---

### Post by Quackers on 2010-08-11
Excellent result Jack. That would be the same line for me too for the 32 bit entry and the one after for the 64 bit. Very,very niiiiiice :-)

---

