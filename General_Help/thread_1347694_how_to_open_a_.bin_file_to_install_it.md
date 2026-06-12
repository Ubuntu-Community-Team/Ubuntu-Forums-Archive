---
title: "how to open a .bin file to install it ?"
date: 2009-12-06
forum: General Help
---

### Post by sexygun on 2009-12-06
i have download the Java Jdk because i"m a Java programmer.
the jdk has come as a .bin file.

so how i install it ? i try the chmod and its don"t work.
i don"t know what to do. help me please ;)

if you ask... i use the Linux Ubuntu-Desktop 9.10 GNome.

---

### Post by whoop on 2009-12-06
What exact commands did you try?
[http://ubuntuforums.org/showthread.php?t=233309](http://ubuntuforums.org/showthread.php?t=233309)

---

### Post by Sam on 2009-12-06
```
chmod +x /path/to/file.bin
sudo /path/to/file.bin
```

OR

```
sudo sh /path/to/file.bin
```

---

### Post by sexygun on 2009-12-06
i do that>>>

```

cd /home/myuser/Downloads
chmod a+x java_ee_sdk-5_08-jdk-6u17-linux.bin
./java_ee_sdk-5_08-jdk-6u17-linux.bin

```but its don"t works.
i get the erorr
```
./java_ee_sdk-5_08-jdk-6u17-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

OR THAT ERORR

> java_ee_sdk-5_08-jdk-6u17-linux.bin: 1: Syntax error: "(" unexpected


---

### Post by whoop on 2009-12-06
> **sexygun said:**
> i do that>>>

```

cd /home/myuser/Downloads
chmod a+x java_ee_sdk-5_08-jdk-6u17-linux.bin
./java_ee_sdk-5_08-jdk-6u17-linux.bin

```but its don"t works.
i get the erorr
```
./java_ee_sdk-5_08-jdk-6u17-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

OR THAT ERORR

Maybe it's because it requires libstdc++.so.5 and you probably have libstdc++.so.6

---

### Post by sexygun on 2009-12-06
so what i need to do ?

---

### Post by whoop on 2009-12-06
> **sexygun said:**
> so what i need to do ?

Is there a newer version of the sdk you can use?

---

### Post by sexygun on 2009-12-06
its the newest !

---

### Post by whoop on 2009-12-06
Someone else has been wrestling with your problem... Maybe reading that can solve your problem:

[http://forums.sun.com/thread.jspa?threadID=5416432](http://forums.sun.com/thread.jspa?threadID=5416432)

---

### Post by stylishgnome on 2009-12-06
As an aside, 

> 
java_ee_sdk-5_08-jdk-6u17-linux.bin: 1: Syntax error: "(" unexpected 


is probably as a result of you trying to invoke a sh-variant with sh. Try:

> 
head -n1 java_ee_sdk-5_08-jdk-6u17-linux.bin
 

to find out which program you should be launching it with (probably bash). In which case you should launch it like this:

> 
bash java_ee_sdk-5_08-jdk-6u17-linux.bin


---

### Post by sexygun on 2009-12-06
don"t works. 
can you give me script to fix that ?
i"m don"t understand...please help me...

---

### Post by Sam on 2009-12-06
What about installing [sun-java6-jdk](apt:sun-java6-jdk) from the repository ?

---

### Post by asahin on 2009-12-07
I got same problem. After a few lines of code, problem solved. I hope it works for you too.
```

sed -i 's/libstdc++.so.5/libstdc++.so.6/g' ./Desktop/java_app_platform_sdk-5_08-jdk-6u17-linux.bin
chmod +x ./Desktop/java_app_platform_sdk-5_08-jdk-6u17-linux.bin
./Desktop/java_app_platform_sdk-5_08-jdk-6u17-linux.bin

```
It replaces missing lib with existing version. I have different package. So you should replace filename with your own

---

### Post by lnpkural on 2009-12-24
asahin it worked great..

1.```
cd /DIRECTORY_OF_THE_FILE
```
2.```
sed -i 's/libstdc++.so.5/libstdc++.so.6/g' ./java_ee_sdk-5_08-jdk-6u17-linux.bin
```
3.```
chmod +x ./java_ee_sdk-5_08-jdk-6u17-linux.bin
```
4.```
./java_ee_sdk-5_08-jdk-6u17-linux.bin
```

---

