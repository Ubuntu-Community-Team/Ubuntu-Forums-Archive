---
title: "loop device cleanup problem"
date: 2011-03-28
forum: General Help
---

### Post by ssouffri on 2011-03-28
Hi,

I have a question about the **losetup** utility for setting up loop devices.
I am having some trouble with cleaning up loop devices. I want to *safely* "detach" all loop devices associated with a certain file (.../disk.img) and only those devices.

Under normal circumstances I can output all these devices with the following command :
```

# losetup -j ".../disk.img"
/dev/loop0: [0806]:15342004 (.../dis*), offset 65536
/dev/loop1: [0806]:15342004 (.../dis*), offset 574324736
/dev/loop2: [0806]:15342004 (.../dis*), offset 576421888

```Notice that the actual file path is rather long and losetup seems to abbreviate it to (.../dis*) in its output.

If the file is somehow deleted, which is possible in my case, the previous command does not output anything anymore. As I would expect. But, given the output of the following command, the devices still appear to be attached to the file in some way.

```

# losetup -a
/dev/loop0: [0806]:15342004 (.../dis*), offset 65536
/dev/loop1: [0806]:15342004 (.../dis*), offset 574324736
/dev/loop2: [0806]:15342004 (.../dis*), offset 576421888

```Since the file name is abbreviated by _*losetup -a*_ and *_losetup -j ".../disk.img"_ *does not output anything I can't tell which loop devices are (or were) associated with my file and thus I can't safely detach them.

Is there a way to clean up my loop devices?
If someone knows a way to create and use device nodes other then /dev/loop*  that would solve my problem as well.

---

