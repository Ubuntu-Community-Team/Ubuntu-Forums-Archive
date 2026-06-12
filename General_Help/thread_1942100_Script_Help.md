---
title: "Script Help"
date: 2012-03-16
forum: General Help
---

### Post by Bobhuber on 2012-03-16
Hey all need a bit of help with a script I writing to automate compiling a new Kernel.
What I'm doing is moving the downloaded file to another directory , extracting it and then I want to change to that directory and compile the kernel. The problem in a nutshell is extracting the first part of a string (the name of the extracted Kernel Directory) so I can change into that directory to finish the process. 
From  > linux-3.3-rc7.tar.bz2
I need  > linux.3.3-rc7 (the name of the directory that is created from the tarball)
I then need to change into that directory.
Heres the script up to that point which while not pretty works.```
#!/bin/bash
echo "Getting ready to compile the new Kernel" 
mv /home/bob/Downloads/*.bz2 /media/secondary/kernels/lean/ &&
cd /media/secondary/kernels/lean &&
a='*.bz2' &&
tar -jxf /media/secondary/kernels/lean/$a &&
```
Appreciate the help.

---

### Post by papibe on 2012-03-16
Hi Bobhuber.

I'm not pretty clear about what you are trying to do. Are you moving and decompresing several tarballs? or just one at a time?

If there are several files you would need to do cycle to go to each one:
```
cd /media/secondary/kernels/lean/

for tarfile in *.bz2; do

    # Get untar directory
    # For instance 'linux-3.3-rc7' from 'linux-3.3-rc7.tar.bz2'
    dir=${tarfile%.tar.bz2}

    cd "$dir"
    # compile
    ...

    # return to the main directory: /media/secondary/kernels/lean/
    cd -
done
```
${tarfile%.tar.bz2} means to take $tarfile and trim the shortest match of 'tar.bz2' from the end. So if $tarfile is "linux-3.3-rc7.tar.bz2" the expresion ${tarfile%.tar.bz2} will became "linux-3.3-rc7".

I hope that helps, and tell us if I misunderstood something.
Regards.

---

### Post by Bobhuber on 2012-03-16
> **papibe said:**
> Hi Bobhuber.


```
cd /media/secondary/kernels/lean/

for tarfile in *.bz2; do

    # Get untar directory
    # For instance 'linux-3.3-rc7' from 'linux-3.3-rc7.tar.bz2'
    dir=${tarfile%.tar.bz2}

    cd "$dir"
    # compile
    ...

    # return to the main directory: /media/secondary/kernels/lean/
    cd -
done
```${tarfile%.tar.bz2} means to take $tarfile and trim the shortest match of 'tar.bz2' from the end. So if $tarfile is "linux-3.3-rc7.tar.bz2" the expresion ${tarfile%.tar.bz2} will became "linux-3.3-rc7".

I hope that helps, and tell us if I misunderstood something.
Regards.
Just doing one file and that's exactly what I was looking for. Thanks very much.

---

### Post by bodhi.zazen on 2012-03-16
> **Bobhuber said:**
> Hey all need a bit of help with a script I writing to automate compiling a new Kernel.
What I'm doing is moving the downloaded file to another directory , extracting it and then I want to change to that directory and compile the kernel. The problem in a nutshell is extracting the first part of a string (the name of the extracted Kernel Directory) so I can change into that directory to finish the process. 
From  > linux-3.3-rc7.tar.bz2
I need  > linux.3.3-rc7 (the name of the directory that is created from the tarball)
I then need to change into that directory.
Heres the script up to that point which while not pretty works.```
#!/bin/bash
echo "Getting ready to compile the new Kernel" 
mv /home/bob/Downloads/*.bz2 /media/secondary/kernels/lean/ &&
cd /media/secondary/kernels/lean &&
a='*.bz2' &&
tar -jxf /media/secondary/kernels/lean/$a &&
```
Appreciate the help.

you can accomplish the same thing with a single line with the -C option for tar.

And as it is a single file, might as well use tab completion. Most kernels are linux-version.tar.bz2 so ...

```
tar xjvf linux<tab> -C /media/secondary/kernels/lean/
```

You also do not need the `&&` in your script.

FWIW, when compiling a kernel, you can simply extract it in your home directory. You then compile it as a user, you do not need to use root until you go to install it.

```
make localmodconfig
make -j5
make -j5 modules
sudo make modules_install
sudo cp arch/x86_64/boot/bzImage /boot/vmlinuz-version
sudo sudo update-initramfs -c -k version
```

---

### Post by Bobhuber on 2012-03-17
> **bodhi.zazen said:**
> you can accomplish the same thing with a single line with the -C option for tar.

And as it is a single file, might as well use tab completion. Most kernels are linux-version.tar.bz2 so ...

```
tar xjvf linux<tab> -C /media/secondary/kernels/lean/
```You also do not need the `&&` in your script.

FWIW, when compiling a kernel, you can simply extract it in your home directory. You then compile it as a user, you do not need to use root until you go to install it.

```
make localmodconfig
make -j5
make -j5 modules
sudo make modules_install
sudo cp arch/x86_64/boot/bzImage /boot/vmlinuz-version
sudo sudo update-initramfs -c -k version
```
 Thanks for the tips. I'm compiling with kpkg on a second drive to save writes on my SSD and executing make and dpkg from there. The && was for my own peace of mind and insecurities with the script completing a section at a time before proceeding . I'm 62 and still learning with the great help from this forum.

---

### Post by Bobhuber on 2012-03-17
Just a followup to let you know everything works great and to post what may be a bug ??
If I execute from within a for-do loop as if there were multiple files the dir variable is correct.There is only one .bz2 file in the directory.
```
for tarfile in *.bz2; do
# For instance 'linux-3.3-rc7' from 'linux-3.3-rc7.tar.bz2'
dir=${tarfile%.tar.bz2}
echo $dir 
linux-3.3-rc7   # (correct)
done
```But if I assign dir a value as in 
```
tarfile='*.bz2'  # or tarfile="*.bz2"
echo $tarfile 
linux-3.3-rc7.tar.bz2 # (correct)  
dir=${tarfile%.tar.bz2} 
echo $dir 
linux-3.3-rc7.tar.bz2  # (wrong)
```It only does this about half of the time. The rest of the time it works correctly with the same commands.

---

### Post by Bobhuber on 2012-03-17
My own fix.

a=$(ls -1 *.bz2) 
dir=${a%.tar.bz2} > now works as it should and picks up the first part of the string (a)

---

### Post by papibe on 2012-03-17
Indeed.

Because if assigned this way:
```
tarfile='*.bz2'  # or tarfile="*.bz2"
```
tarfile actually is:
```
echo "$tarfile"
*.bz2
```
Only when left 'free' for shell to expand you have:
```
echo $tarfile
linux-3.3-rc7.tar.bz2
```
An easy way to solve would be:
```
tarfile=$(echo *.bz2)
```
That way in both cases:
```
echo $tarfile
linux-3.3-rc7.tar.bz2

echo "$tarfile"
linux-3.3-rc7.tar.bz2
```
work as you expect.

Hope that helps.
Regards.

---

### Post by bodhi.zazen on 2012-03-17
Just a FYI ...

Neither of those solutions will work if the archive has a space in the name =)

---

