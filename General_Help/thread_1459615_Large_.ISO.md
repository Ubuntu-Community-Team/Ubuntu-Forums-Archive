---
title: "Large .ISO"
date: 2010-04-21
forum: General Help
---

### Post by Hman242 on 2010-04-21
I have a large .iso file, approximately 7.5GB. I need to transfer it from one computer of mine to another. If I burn the .iso to multiple disks, is it possible to recombine the file later on?

---

### Post by lisati on 2010-04-21
My own preference would be to put it on a DL disk if I had one available.

---

### Post by Hman242 on 2010-04-21
The largest storage medium I have is a standard DVD-RW.

---

### Post by sisco311 on 2010-04-21
Yep:
```
split -b 4300M big.iso
```
to reassemble, use cat:
```
cat xa* > big.iso
```

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files)

---

### Post by Hman242 on 2010-04-21
The other computer doesn't have Linux installed, it is a Windows computer.

---

### Post by sisco311 on 2010-04-21
> **Hman242 said:**
> The other computer doesn't have Linux installed, it is a Windows computer.

Uh, I'm not sure about the syntax, but in cmd.exe you can run something like:
```
copy /b file1 + file2 + file3 big.iso
```

maybe something like:
```
copy /b xa*+ big.iso
```
sorry, I don't have Windows, can't test it.

---

### Post by srs5694 on 2010-04-21
Many archive formats, including tar, zip, and rar, support multi-file archives. Try investigating whichever of these you've got on both Windows and Linux, or that you can most easily install on both platforms, to see how to do the job. With zip, you'd do this:

```

zip -s 4g zipfile.zip foo.iso

```

This should produce as many 4GB or smaller files as necessary to hold foo.iso. The files will be called zipfile.z01, zipfile.z02, and so on up to zipfile.zip. In your case it'll probably be only two files (maybe just one), depending on whether the .iso file contains precompressed data. If you get three files, you can fine-tune the -s option or put the smallest zip file along with one of the big ones on one DVD-RW to get it all on two discs.

---

### Post by undecim on 2010-04-21
7zip allows you to split up files easily. It goes up to 1000MB pieces I think, but you can put 4 on a DVD.

Then you can open it back up on any system with 7zip.

---

### Post by Hman242 on 2010-04-22
Thanks for those codes, I was able to successfully split and recombine the file. However, I am having a problem that might be related.

When I try to run a .exe that was in the .iso, it says "Not a Valid Win32 Application". I've heard of many reasons that this can be caused by, and I'm wondering if the splitting and recombining could have caused this. Any help?

---

### Post by undecim on 2010-04-23
> **Hman242 said:**
> Thanks for those codes, I was able to successfully split and recombine the file. However, I am having a problem that might be related.

When I try to run a .exe that was in the .iso, it says "Not a Valid Win32 Application". I've heard of many reasons that this can be caused by, and I'm wondering if the splitting and recombining could have caused this. Any help?
Did you verify the MD5 of the .iso after transferring it?

---

### Post by nl4m on 2010-04-23
Why don't you try to FTP the file? I think it should work even from a Linux to a Windows machine. I can tell you from experience that you can FTP files from you Xbox to your Windows machine. If Xbox's OS is windows compatible Linux has to be to.

---

### Post by undecim on 2010-04-24
> **nl4m said:**
> Why don't you try to FTP the file? I think it should work even from a Linux to a Windows machine. I can tell you from experience that you can FTP files from you Xbox to your Windows machine. If Xbox's OS is windows compatible Linux has to be to.

The Xbox is made by Microsoft, so one would expect them to be compatible.

FTP is pretty much universal though. There's also shared folders, but over the network might be a slow transfer.

---

