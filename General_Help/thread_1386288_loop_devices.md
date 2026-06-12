---
title: "loop devices"
date: 2010-01-20
forum: General Help
---

### Post by snorkytheweasel on 2010-01-20
I'm working on a project in which my end users will access Windows programs that run from a CD. My brainstorm is to convert the CDs to ISO files, and store/manage those ISOs as loop devices on an Ubuntu server. 

I know how to do this on a Windows server, but, well, you know....;)

One of the limitations in Windows is that for all practical purposes you max out at approximately 20 'virtual CDs', and the good free software to do this maxes out at 8 devices. I'd prefer to use a linux server because of linux's lower demands on resources and (of course) cost.

[LIST=1]
[*]My assumption is that the files on the loop devices can be ISOs. Is that a reasonable assumption?

[*]If I use an Ubuntu Server to operate the loop devices, and if the content is Windows software, can my Windows users run that software?

[*]What is the maximum number of loop devices I can have on a 32-bit server? On a 64-bit server? I assume that the devices would be numbered loop0, loop1, loop2, and so on...

[*]If I'm on the right track here, how would Windows workstations access the virtual devices, i.e., what command line command would they use to access loop3? Or could the access be more direct, i.e., a click on a "filename" in Windows Explorer - a mounted device such as /dev/loop5 ?

[*]What is a good source for documentation on loop devices?

[*]The part about the software being Windows software is non-negotiable. How I enable the end users to run this is flexible - but I *always* prefer a linux solution.
[/LIST]

---

### Post by kitserve on 2010-01-21
Hello snorky, 

I'm not sure if I've entirely understood your request, but here goes. You are correct, it is possible to mount CD images in Linux. The command 'mount -o loop file.iso /mount/directory' should do the job. The contents of the CD image will then be visible in /mount/directory. 

For the rest of your request, it really depends on how complicated the functionality you require is. It would be relatively straightforward to share the CD image mount points as samba shares on the network, that way the Windows clients will be able to access the shares and see the contents of the CDs. However, if they use some kind of protection and you need them to appear as virtual CD drives then I think you will be out of luck. 

If this is the case, you would probably have more success just sticking all the iso files in a samba share on the Linux server and then installing something like PowerISO or Daemon Tools on the client machines and use them to mount the CD images from the network share. 

I'm afraid I don't know of any in dept documentation on loop devices off the top of my head. This is not to say there isn't any, it's just that I've picked everything from the man pages and searching online. I don't know what the limit on the number of loop devices is, but I expect it is pretty high - how many do you expect to need?

---

### Post by sisco311 on 2010-01-22
> **kitserve said:**
> 

I'm not sure if I've entirely understood your request, but here goes. You are correct, it is possible to mount CD images in Linux. The command 'mount -o loop file.iso /mount/directory' should do the job. The contents of the CD image will then be visible in /mount/directory. 



```
mount -o loop iso.iso /mount/point
```
associates the .iso with a loop device node (i.e. /dev/loop0)
& mounts the device at the mount point.

it's the same as:
```

losetup /dev/loop0 iso.iso
mount /dev/loop0 /mount/point
```

You can change the maximum number of loop devices(8 by default) with the max_loop=<number> kernel parameter or you can manually create a new loop device at runtime:
```
mknod -m0660 /dev/loop9 b 7 9
chown root.disk /dev/loop9
```

I'm not sure if you can directly access the loop devices from Windows, but you can mount them in Linux and share the mount point.

---

### Post by kitserve on 2010-01-25
Well, I don't know about the OP, but I found that informative, thanks sisco311!

---

