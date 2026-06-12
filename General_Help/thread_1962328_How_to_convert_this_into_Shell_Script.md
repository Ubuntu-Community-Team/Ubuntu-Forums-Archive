---
title: "How to convert this into Shell Script"
date: 2012-04-20
forum: General Help
---

### Post by juanlansang on 2012-04-20
Good day everyone!

I am new to Ubuntu specifically in shell scripting. I would like to ask how or what is the equivalent of this batch file to a shell script.
[B]
echo off

cls

pushd \\JO501\d\Soft\ABC

java -jar Aqua.jar

echo on[/B]

JO501 - Computer Name [ Windows OS ] in drive "d", folder Soft the folder ABC


I hope someone could help me with this problem. And I would like also to ask if it is possible that I can run a file from UBUNTU to a Windows network like JAR files.

---

### Post by idoitprone on 2012-04-21
> **juanlansang said:**
> Good day everyone!

I am new to Ubuntu specifically in shell scripting. I would like to ask how or what is the equivalent of this batch file to a shell script.
[B]
echo off

cls

pushd \\JO501\d\Soft\ABC

java -jar Aqua.jar

echo on[/B]

JO501 - Computer Name [ Windows OS ] in drive "d", folder Soft the folder ABC


I hope someone could help me with this problem. And I would like also to ask if it is possible that I can run a file from UBUNTU to a Windows network like JAR files.

I do not know what does the echo off do
but I guess I can help with the rest

Window commands and linux commands about the same

cls = clear
pushd is about the same
java -jar should be the same

```
#!/bin/bash
clear
pushd /JO501/d/Soft/ABC
java -jar Aqua.jar &  
popd

```I am not sure where is the directory located on the network, so dont ask me
I only gave your the basic equivelent

---

