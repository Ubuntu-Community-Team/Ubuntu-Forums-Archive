---
title: "trying to install true audio ttaenc and having problems"
date: 2010-01-10
forum: General Help
---

### Post by shantiq on 2010-01-10
[B][COLOR=Navy]well i am on ubuntu karmic koala and i have been trying to install true audio codec ttaenc

the file we have is   ttaenc-3.4.1-src   this came directly from aleksandr djuric who looks after true audio



now he tells me to use    ```
Compilation and installing
(your work dir) - the path where you have unpacked the codec sources

$ su -
# cd /(your work dir)/ttaenc-3.4.1-src
# make; make install

```
to install it     so i modified that for ubuntu and this is what i got[/COLOR][/B]  


```
shantiq@shantiq-desktop:~$ cd ./ttaenc-3.4.1-src
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make
make: `ttaenc' is up to date.
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
install: cannot remove `/usr/bin/ttaenc': Permission denied
make: *** [install] Error 1
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ sudo make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ 


```[COLOR=Navy][B]

any ideas as to how to progress from there?


will also post in multimedia as i am not sure whether this is general help or multimedia specific


thanx in advance for all useful help[/B][/COLOR]

---

### Post by shantiq on 2010-01-10
[[COLOR=Blue]**all sorted  **[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1377265")

[COLOR=Blue][B]hopefully this will help someone else sometime


the answer was

do not use ./configure


just   make and make install


;););)
[/B][/COLOR]

---

