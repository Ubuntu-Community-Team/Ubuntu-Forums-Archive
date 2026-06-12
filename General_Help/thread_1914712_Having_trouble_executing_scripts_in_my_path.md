---
title: "Having trouble executing scripts in my path"
date: 2012-01-24
forum: General Help
---

### Post by rwgast on 2012-01-24
Ok so i have set up a directory called home/robert/Android/scripts I then added it to my path via the .bashrc as i do with all of my dev tools. here is a listing of of the directory with permissions

```
drwxrwxr-x 2 robert robert  4096 2012-01-24 17:38 .
drwxrwxr-x 9 robert robert  4096 2012-01-24 17:46 ..
-rwxr-xr-x 1 robert robert   744 2009-05-01 04:28 extract-kernel.pl
-rwxr-xr-x 1 robert robert  1248 2009-05-01 04:28 extract-ramdisk.pl
-rwxr-xr-x 1 robert robert 24302 2009-09-20 11:05 mkbootfs
-rwxr-xr-x 1 robert robert 23798 2009-09-20 11:05 mkbootimg
-rwxr-xr-x 1 robert robert  5596 2010-03-04 04:16 unyaffs
```

when in the directory i can run ./extract-kernel.pl with no problems at all! When i leave the scripts directory the script wont run i get this message

```
robert@logicdesign:~/Android/kernel_image$ ./extract-kernel.pl 
bash: ./extract-kernel.pl: No such file or directory

```

which is really strange because not only is the directory included in my path here is the listing

```
robert@logicdesign:~/Android/kernel_image$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/robert/Android/android-sdk-linux/tools:/home/robert/Android/android-sdk-linux/platform-tools:/home/robert/Android/android-ndk-r7/toolchains/arm-linux-androideabi-4.4.3/prebuilt/linux-x86/bin:/home/robert/Android/scripts:/home/robert/Android/scripts

```

but if i i run something like mkbootimg which is a binary in the same path with the same permissions it runs just fine!!  I can run the script right now by using the command 

```
 perl /home/robert/Android/scripts/extract-kernel.pl
```

but obviously this isn't the ideal way to do it does anyone know whats going on?

---

### Post by redmk2 on 2012-01-24
```
./extract-kernel.pl
```
This means run this script in this directory.  The ./ says this.  If you are in any other directory the executable is not in that directory.  The path statement is also irrelevant.

If the path is correct then you should get the proper results from anywhere with just this statement from the CLI```
extract-kernel.pl
```

FYI if you look in any directory you will see this ```
.
..
```
These are the names for: *this directory* (.) and *the directory above* (..).

That's why this will move you up one directory```
cd ..
```

---

