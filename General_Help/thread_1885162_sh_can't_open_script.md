---
title: "sh can't open script?"
date: 2011-11-22
forum: General Help
---

### Post by Los Frijoles on 2011-11-22
I am in the process of installing the Altera Quartus II Web Edition software. It comes in a gigantic 3GB shell script. However, even after giving permissions to execute and stuff I cannot get the install to run. Here is what I get:

```
kcuzner@kcuzner-AOA150:~/Downloads$ ll
total 3187816
-rwxrwxrwx 1 kcuzner kcuzner 3203561074 2011-11-22 08:44 11.1_173_quartus_free_linux.sh
....
kcuzner@kcuzner-AOA150:~/Downloads$ sh /home/kcuzner/Downloads/11.1_173_quartus_free_linux.sh 
sh: Can't open /home/kcuzner/Downloads/11.1_173_quartus_free_linux.sh
kcuzner@kcuzner-AOA150:~/Downloads$ sh ./11.1_173_quartus_free_linux.sh 
sh: Can't open ./11.1_173_quartus_free_linux.sh
kcuzner@kcuzner-AOA150:~/Downloads$ sh 11.1_173_quartus_free_linux.sh 
sh: Can't open 11.1_173_quartus_free_linux.sh
kcuzner@kcuzner-AOA150:~/Downloads$ ./11.1_173_quartus_free_linux.sh 
/bin/sh: Can't open ./11.1_173_quartus_free_linux.sh

```

Is there something I am missing here? The only thing I can think of is that my home directory is encrypted.

---

### Post by mutley89 on 2011-11-22
what does "file 11.1_173_quartus_free_linux.sh" give you? Also you can read the file with "less filename" .  Post the first few lines with "head -n 20 filename".  It's probably some form of archive wrapped with a few lines to extract/copy it.

---

### Post by dandnsmith on 2011-11-22
Is the file marked as executable?

---

### Post by satanselbow on 2011-11-22
and just to complete the set... you might want to run it as sudo - though it may prompt you as required ;)

to make executable (though from your orig post it is already!):
```

chmod 700 ./filename.sh

```

to run:
```
sudo sh ./filename.sh
```

Afterthought:
Given the size of the thing it may be corrupt - is there an md5 on the site to check it against?

---

### Post by TyphoonJoe on 2011-11-22
Do you get the exact same error if you run this? :
```
sh nonexistingscript.sh
```

If so, can you share the output of:
```
ls -al /home/kcuzner/Downloads/11.1_173_quartus_free_linux.sh
```

Your ll command will list all files in the directory, if there is a control character in the filename this ls command should show the error.  

It may also be that your process has a limit on the size of files it can open.  Can you share the output of "ulimit -a" ?  There is a file limit that may be limiting your access. If this is lower than 3 GB you could use sudo or change the limit.

---

### Post by SeijiSensei on 2011-11-22
deleted

---

### Post by Los Frijoles on 2011-11-22
Thanks for all the replies.

So, the file is executable (I chmodded 777...I know that's bad to do but I was just making sure).

Here is the result of doing the non-existant file check thing. quartus.sh is the now renamed install script, test.sh is a file containing "#!/bin/sh [newline]echo hi", and asdf is the non existant file.
```
kcuzner@kcuzner-AOA150:/tmp$ ll
total 3128516
drwx------ 2 kcuzner kcuzner       4096 2011-11-22 10:58 keyring-FXvTyI
drwx------ 2 lightdm lightdm       4096 2011-11-22 10:59 pulse-2L9K88eMlGn7
drwx------ 2 kcuzner kcuzner       4096 2011-11-22 10:58 pulse-cXyHZzsRwpC5
drwx------ 2 root    root          4096 2011-11-22 10:53 pulse-PKdhtXMmr18n
-rwxrwxr-x 1 kcuzner kcuzner 3203561074 2011-11-22 15:53 quartus.sh
drwx------ 3 kcuzner kcuzner       4096 2011-11-22 10:59 sni-qt_skype_1892-VX4MRI
drwx------ 2 kcuzner kcuzner       4096 2011-11-22 10:58 ssh-YzonKnLb1785
-rwxrwxr-x 1 kcuzner kcuzner         21 2011-11-22 21:47 test.sh
-rw-rw-r-- 1 lightdm lightdm          0 2011-11-22 10:53 unity_support_test.0
drwx------ 2 kcuzner kcuzner       4096 2011-11-22 10:58 virtual-kcuzner.IokbST
kcuzner@kcuzner-AOA150:/tmp$ sh test.sh
hi
kcuzner@kcuzner-AOA150:/tmp$ sh ./test.sh
hi
kcuzner@kcuzner-AOA150:/tmp$ sh asdf
sh: Can't open asdf
kcuzner@kcuzner-AOA150:/tmp$ sh ./asdf
sh: Can't open ./asdf
kcuzner@kcuzner-AOA150:/tmp$ sh quartus.sh
sh: Can't open quartus.sh
kcuzner@kcuzner-AOA150:/tmp$ sh ./quartus.sh
sh: Can't open ./quartus.sh
kcuzner@kcuzner-AOA150:/tmp$ sh
$ sh asdf
sh: Can't open asdf
$ sh ./asdf
sh: Can't open ./asdf
$ ./asdf
sh: ./asdf: not found
$ ./quartus.sh
/bin/sh: Can't open ./quartus.sh
$ exit
```

Executing "head -20" on the script returns the following:
```
kcuzner@kcuzner-AOA150:/tmp$ head -20 quartus.sh 
#!/bin/sh
# This script was generated using Makeself 2.1.5

CRCsum="4090133961"
MD5="f3a01db471ea54958c48629f0f773776"
TMPROOT=${TMPDIR:=/tmp}
export PATH=.:webinstall:$PATH
export LD_LIBRARY_PATH=.:webinstall:$LD_LIBRARY_PATH

label="Quartus II Web Edition (Free)"
script="setup"
scriptargs=""
targetdir="11.1_173_quartus_free_linux"
filesizes="3203551460"
keep=y

print_cmd_arg=""
if type printf > /dev/null; then
    print_cmd="printf"
elif test -x /usr/ucb/echo; then
```
So I guess it is an extractor.

Now, here is something weird I discovered. If I do "bash quartus.sh" I get the following:
```
kcuzner@kcuzner-AOA150:/tmp$ bash quartus.sh 
Creating directory 11.1_173_quartus_free_linux
Verifying archive integrity... All good.
Uncompressing Quartus II Web Edition (Free)...................................................................................................................................................................................................
./setup: 1: Syntax error: "&" unexpected
```
It took about 15-20 minutes to get to that point. I suspect that the error has something to do with using bash instead of dash.

I also ran md5 against it (there was a provided hash at the download site) and it matched up so the download is intact.

---

### Post by mutley89 on 2011-11-23
Bash should run all sh scripts, on most non debian linux systems sh is a symlink to bash anyway.
Some info here concerning "makeself" :
[http://megastep.org/makeself/](http://megastep.org/makeself/)
Basically it creates a tarball and a few lines to extract it and then run commands on the result. I think you should now have a directory containing the extracted contents of the tarball.  Could you post the original script up to the point where the data starts (it will probably show as mostly escape sequences), and also the "setup" script (I think this will be either under /tmp or the "11.1_173_quartus_free_linux" subdirectory, assuming you haven't rebooted since then).

---

### Post by Los Frijoles on 2011-11-23
The setup file: [http://pastebin.com/2anxFzwp](http://pastebin.com/2anxFzwp)

I have a feeling that the |& on line 19 isn't right...I've never seen an "or-and" before (or course, for all I know its just a boolean function I've never used). However, when I change it to || the error changes to "28: bad substitution".

Edit: SOLVED! Ok, so on a whim I decided to run "bash setup". It worked! So here is the problem: the scripts all did #!/bin/sh which on my computer redirects to dash. The scripts are written for bash! So, for people who browse this later the solution is to change the symbolic link /bin/sh to bash (and if you would like, change it back when done).

---

### Post by mutley89 on 2011-11-23
Glad you solved it, as an aside "|&" is not a boolean operator, it is a bash specific way of redirecting stderr though a pipe. See here for a full explanation:
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

