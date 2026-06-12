---
title: "Sh problems"
date: 2009-12-14
forum: General Help
---

### Post by bluestar14 on 2009-12-14
whenever i try to extract a .bin file(sh nameoffile.bin) it says:
```
avin@STUDYROOML:~/Downloads$ sh java_ee_sdk-5_01-linux.bin
java_ee_sdk-5_01-linux.bin: 1: Syntax error: "(" unexpected
```

---

### Post by NoaHall on 2009-12-14
sh isn't a extracting program, it's a shell language interpreter. To run a .bin file, all you need to do is enter the full location and press enter.

---

### Post by bluestar14 on 2009-12-14
still won't work, i tried:
```
avin@STUDYROOML:~/Downloads$ ~/Downloads/java_ee_sdk-5_01-linux.bin
/home/avin/Downloads/java_ee_sdk-5_01-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

---

### Post by japju on 2009-12-14
Try

```
./java_ee_sdk-5_01-linux.bin

```

---

### Post by bluestar14 on 2009-12-14
it shows same thing as said above

---

### Post by NoaHall on 2009-12-14
You need to install libstdc++.so.5. Run ```
apt-cache search libstdc++
``` Then see if the version is there. If you have gcc++ installed, it should also be installed. You might want to run ```
sudo ldconfig
```

---

### Post by earthpigg on 2009-12-14
mind showing us this .bin file?

```
cat ~/Downloads/java_ee_sdk-5_01-linux.bin
```

if it's all gobbeldy-gook, then that wont be helpful.... but if its just a script of some sort (meaning you will see letters and numbers and stuff), it may shed some light on the situation.

---

### Post by NoaHall on 2009-12-14
> **earthpigg said:**
> mind showing us this .bin file?

```
cat ~/Downloads/java_ee_sdk-5_01-linux.bin
```

if it's all gobbeldy-gook, then that wont be helpful.... but if its just a script of some sort (meaning you will see letters and numbers and stuff), it may shed some light on the situation.

He's trying to install the java sdk file by the looks of it.

---

### Post by bluestar14 on 2009-12-14
well, its gobbely-gork

---

### Post by bluestar14 on 2009-12-14
> **NoaHall said:**
> You need to install libstdc++.so.5. Run ```
apt-cache search libstdc++
``` Then see if the version is there. If you have gcc++ installed, it should also be installed. You might want to run ```
sudo ldconfig
```
The version isn't there

---

### Post by NoaHall on 2009-12-14
> **bluestar14 said:**
> The version isn't there

What is the output? I'm not on Ubuntu right now, so I can't check

Try
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Maybe something needed updating.

---

### Post by bluestar14 on 2009-12-14
well, here is the output:
```
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
lib64stdc++6-4.4-dbg - The GNU Standard C++ Library v3 (debugging files)
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.4-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.4-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.4-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.4-pic - The GNU Standard C++ Library v3 (shared library subset kit)
lib64stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.2-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.2-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.2-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)

```

---

### Post by bluestar14 on 2009-12-14
i tired the update, but nothing was installed/upgraded

---

### Post by NoaHall on 2009-12-14
Okay, try this -
```
ls -a /usr/lib | grep libstdc++.so
```
Post the output, and I'll tell you the next command, based on the output.

---

### Post by bluestar14 on 2009-12-14
here is the output for that:
```
avin@STUDYROOML:~$ ls -a /usr/lib | grep libstdc++.so
libstdc++.so.6
libstdc++.so.6.0.13
```

---

### Post by NoaHall on 2009-12-14
> **bluestar14 said:**
> here is the output for that:
```
avin@STUDYROOML:~$ ls -a /usr/lib | grep libstdc++.so
libstdc++.so.6
libstdc++.so.6.0.13
```

Now try 
```
ln -s /usr/lib/libstdc++.so.6.0.13 /usr/lib/libstdc++.so.5
``` and then try to run the file you're trying to install.

---

### Post by bluestar14 on 2009-12-14
success!!!

---

### Post by NoaHall on 2009-12-14
Great! Mark this thread as solved, and let me know if you've got any more problems.

---

### Post by japju on 2009-12-14
Not JDK, but Enterprise Edition (EE).......

---

### Post by princemanjee on 2009-12-20
> **NoaHall said:**
> Now try 
```
ln -s /usr/lib/libstdc++.so.6.0.13 /usr/lib/libstdc++.so.5
``` and then try to run the file you're trying to install.

THANK YOU YOU HACKER YOU! Worked like a charm...

---

