---
title: "Which files are missing from a sequence?"
date: 2012-02-22
forum: General Help
---

### Post by angryhomer17 on 2012-02-22
I have a folder of pictures sequentially numbered from 0001 to 2128. The folder has 2118 items; 10 pictures are not there. How can I easily find out which files are missing from the sequence? Thanks.

---

### Post by surfer on 2012-02-22
in bash, this might help.

```
for nr in $(seq 1 2118); do printf -v fle "%04i.jpeg" ${nr}; if ! [ -e  "${fle}" ]; then echo "${fle}" missing; else echo "${fle} exists";  fi;  done

```

you may need to remove the 'exists' print and adapt the file name extension (.jpeg) to whatever your pictures are called.

---

### Post by Vaphell on 2012-02-22
bash can create ranges just fine, without external seq command.
```
for f in pic{0001..2128}.jpg; do if [ ! -f "$f" ]; then echo "$f"; fi; done
```
pic{0001..2128}.jpg will get expanded to the list of files from pic0001.jpg to pic2128.jpg

---

### Post by surfer on 2012-02-22
nice! didn't know that this would also work with 'formatting' (such as 0001). thanks!

---

### Post by Vaphell on 2012-02-22
afaik ranges with 0-padding were implemented rather recently and other shells don't necessarily have it, so it's pretty much bash specific. If that feature is unavailable then you need to use printf with the {1..n} range

---

### Post by Khayyam on 2012-02-22
> **Vaphell said:**
> afaik ranges with 0-padding were implemented rather recently and other shells don't necessarily have it, so it's pretty much bash specific.

vaphell ...

This is not true of zsh, though I don't remember it being introduced.

```
% echo $SHELL
/bin/zsh
% zsh --version | awk '{print $1,$2}'
zsh 4.3.10
% for f in pic{01..05}.jpg; do if [[ ! -f "${f}" ]]; then echo "${f}"; fi; done
pic01.jpg
pic02.jpg
pic03.jpg
pic04.jpg
pic05.jpg
```

best ... khay

---

### Post by angryhomer17 on 2012-02-22
> **surfer said:**
> in bash, this might help.

```
for nr in $(seq 1 2118); do printf -v fle "%04i.jpeg" ${nr}; if ! [ -e  "${fle}" ]; then echo "${fle}" missing; else echo "${fle} exists";  fi;  done

```

you may need to remove the 'exists' print and adapt the file name extension (.jpeg) to whatever your pictures are called.

I adapted this to show only my missing png files. It works great. Thanks. 

```
for nr in $(seq 1 2118); do printf -v fle "%04i.png" ${nr}; if ! [ -e  "${fle}" ]; then echo "${fle}" missing; fi;  done
```

---

