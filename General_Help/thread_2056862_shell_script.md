---
title: "shell script"
date: 2012-09-12
forum: General Help
---

### Post by nagileon on 2012-09-12
Hi there.
For loop in Ubuntu works fine directly from the command line. But it doesn't when placed in the shell script.
Any ideas anyone ?


user@server:~/wtest# for i in {1..10};do echo "$i";done
1
2
3
4
5
6
7
8
9
10

cat script.sh
#!/bin/bash
for i in {1..10};do echo "$i";done

user@server:~/wtest# sh script.sh
{1..10}

---

### Post by SlugSlug on 2012-09-12
try 
./script 

not 

sh script

---

### Post by raja.genupula on 2012-09-12
> **SlugSlug said:**
> try 
./script 

not 

sh script

+1 and sh you have to use if your running your script from Other file systems like NTFS FAT etc

---

### Post by nagileon on 2012-09-12
Thanks.
I have figured it out already. But I am sure scripts were working in the old days when preceded with "sh".
Looks to me like another werid change in the system.
Warmest regards,
Peter

---

### Post by Vaphell on 2012-09-12
the deal is that bash and dash (sh) have a different set of features and not everything is going to work if you try *sh bash_script.sh*. Just use #! line to define shell and run the script without calling shell explicitly.

---

### Post by spjackson on 2012-09-12
> **nagileon said:**
> Thanks.
I have figured it out already. But I am sure scripts were working in the old days when preceded with "sh".
Looks to me like another werid change in the system.

A sh script can be executed by
```

sh scriptname

```
but for a bash script you would need
```

bash scriptname

```
Nothing has changed here. Your original result was obtained by sh interpreting the script according to its own syntax and semantics, but you want it to be interpreted by bash.

Note that the shebang (line 1 of your script) is only effective when invoking the program directly by name (e.g. ./scriptname ). It has no effect if you put the name of the interpreter at the start of the command.

---

### Post by nagileon on 2012-09-12
One more question:

How do I get rid of the colorization info from a variable:

 rvc user@server --cmd "vm.on /server/dev/computers/mycluster/resourcePool/pools/PoolX/vms/$thevm" --cmd "exit"

no matches for "/server/dev/computers/mycluster/resourcePool/pools/PoolX/vms/XYZ.pool.local-PoolX\e[0m"

I should get: XYZ.pool.local-PoolX

But the clorization infor is attached to the variable for some strange reason.

---

