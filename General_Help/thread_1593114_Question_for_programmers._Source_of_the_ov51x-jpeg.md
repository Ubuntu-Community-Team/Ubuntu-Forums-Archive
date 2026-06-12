---
title: "Question for programmers. Source of the ov51x-jpeg-core.c"
date: 2010-10-11
forum: General Help
---

### Post by tetris9999 on 2010-10-11
[B]Hello, I am trying to make that driver, but no success so far. There is something, but I am not a programmer, and it is virtually impossible for me to understand the code. When I was first tried to build I got a bunch of errors like these : 
[/B]  
 make[3]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o
[COLOR=Blue]/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function
‘create_proc_ov511_cam’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:677: error: implicit
declaration of function ‘info’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:681: error: ‘struct
proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:689: error: ‘struct
proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:700: error: ‘struct
proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:712: error: ‘struct
proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function
‘proc_ov511_create’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:766: error: ‘struct
proc_dir_entry’ has no member named ‘owner’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function
‘ov51x_clear_snapshot’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:1691: error: implicit
declaration of function ‘warn’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function
‘ov51x_v4l1_ioctl’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing
argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but
argument is of type ‘struct inode *’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing
argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but
argument is of type ‘struct file *’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: warning: passing
argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but
argument is of type ‘long unsigned int’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6386: error: too many
arguments to function ‘video_usercopy’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: At top level:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6651: warning:
initialization from incompatible pointer type[/COLOR]
make[4]: *** [/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov51x-jpeg] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make: *** [kdist_build] Error 2
BUILD FAILED!
 
**after applying this patch **[B][http://www.afallenhope.com/files/ov51x-jpeg.patch](http://www.afallenhope.com/files/ov51x-jpeg.patch) 
I got some errors like this :

[/B]patching file ov51x-jpeg-1.5.9_patched/ov51x-jpeg-core.c
Hunk #1 FAILED at 12.
Hunk #2 FAILED at 539.
Hunk #3 FAILED at 678.
Hunk #4 FAILED at 686.
Hunk #5 FAILED at 697.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 762.
Hunk #8 FAILED at 5733.
Hunk #9 FAILED at 5804.
Hunk #10 FAILED at 5850.
Hunk #11 FAILED at 6355.
Hunk #12 FAILED at 6372.
Hunk #13 FAILED at 6383.
Hunk #14 FAILED at 6624.
Hunk #15 FAILED at 8374.[B]

but, did the patch manually and the errors were reduce to this :
[/B]
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/krum/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
[COLOR=Blue]/home/krum/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/krum/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/krum/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/krum/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1685: error: implicit declaration of function ‘warn’[/COLOR]

[B]this is the create_proc_ov511_cam function from the ov51x-jpeg-core.c file 

[/B]static void
create_proc_ov511_cam(struct usb_ov511 *ov)
{
    char dirname[10];

    if (!ov51x_jpeg_proc_entry || !ov)
        return;

    /* Create per-device directory */
    snprintf(dirname, 10, "%d", ov->vdev->minor);
    PDEBUG(4, "creating /proc/ov51x-jpeg/ov51x/%s/", dirname);
    ov->proc_devdir = create_proc_entry(dirname, S_IFDIR, ov51x_jpeg_proc_entry);
     if (!ov->proc_devdir)
         return;
    
    /* Create "info" entry (human readable device information) */
    PDEBUG(4, "creating /proc/ov51x-jpeg/ov51x/%s/info", dirname);
    ov->proc_info = create_proc_read_entry("info", S_IFREG|S_IRUGO|S_IWUSR,
        ov->proc_devdir, ov511_read_proc_info, ov);
     if (!ov->proc_info)
         return;
    
    /* Don't create it if old snapshot mode on (would cause race cond.) */
    if (!snapshot) {
        /* Create "button" entry (snapshot button status) */
        PDEBUG(4, "creating /proc/ov51x-jpeg/ov51x/%s/button", dirname);
        ov->proc_button = create_proc_read_entry("button",
            S_IFREG|S_IRUGO|S_IWUSR, ov->proc_devdir,
            ov511_read_proc_button, ov);
        if (!ov->proc_button)
            return;
    }

    /* Create "control" entry (ioctl() interface) */
    PDEBUG(4, "creating /proc/ov51x-jpeg/ov51x/%s/control", dirname);
    lock_kernel();
    ov->proc_control = create_proc_entry("control",    S_IFREG|S_IRUGO|S_IWUSR,
        ov->proc_devdir);
    if (!ov->proc_control) {
        unlock_kernel();
        return;
    }
    ov->proc_control->data = ov;
    ov->proc_control->proc_fops = &ov511_control_fops;
    unlock_kernel();
}
[B]
and the ov51x_clear_snapshot function from the same file  [/B]

/* Resets the hardware snapshot button */
static void
ov51x_clear_snapshot(struct usb_ov511 *ov)
{
    switch (ov->bclass) {
        case BCL_OV511:
            reg_w(ov, R51x_SYS_SNAP, 0x00);
            reg_w(ov, R51x_SYS_SNAP, 0x02);
            reg_w(ov, R51x_SYS_SNAP, 0x00);
        case BCL_OV518:
           ** warn**("snapshot reset not supported yet on OV518(+)");
        case BCL_OV519:
            /* Nothing to do ? */
        default:
            err("clear snap: invalid bridge type");
    }
}

**could anyone help me how to alter the code so these two errors to disappear and what is the reason for those? The distro is Lucid 10.04, kernel 2.6.32-25-generic. Thanks**

---

### Post by dino99 on 2010-10-11
you are not the first having issue with this:

[http://www.google.com/search?client=ubuntu&channel=fs&q=ov51x-jpeg-core.c&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ov51x-jpeg-core.c&ie=utf-8&oe=utf-8)

---

