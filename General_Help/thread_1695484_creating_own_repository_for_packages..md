---
title: "creating own repository for packages."
date: 2011-02-25
forum: General Help
---

### Post by utkarshjadhav on 2011-02-25
[COLOR=Red][B]using 10.04 .
I am trying to create my own repository for packages[/B].[/COLOR]So that updates can be done offline. 
1.I copied all packages which i usually use from 
```

/var/cache/apt/archives

```and put it in folder local_repository
2.took backup for of sources.list
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak

```3.did the following at that PATH 
```

echo 'deb file:/PATH/local_repository ./' >  /etc/apt/sources.list

```4.then tried 
```

sudo apt-get update

```But the error comes-
No Packages.gz in the  /PATH/local_repository ./

[B][COLOR=Red]So how to create Packages.gz 
and how to create repository?[/COLOR][/B]

Please help.

---

### Post by stinkeye on 2011-02-26
You probably need to install **build-essential**  and then run 
```
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
from within your **local_repository** directory
to make repo able to be used by synaptic.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10459931&postcount=5")

---

### Post by utkarshjadhav on 2011-02-26
I tried with 
```

utkarsh@utkarsh-laptop:~/Desktop/local_repository$ sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

```
output is-
```

dpkg-scanpackages: info: Wrote 0 entries to output Packages file.

```

What to do?:confused:

---

### Post by stinkeye on 2011-02-27
Did you copy all the deb files from **/var/cache/apt/archives** to 
[B]~/Desktop/local_repository
[/B] ?


...and did you install **build-essential** ?
```
sudo apt-get install build-essential 
```


Just copy the folder **/var/cache/apt/archives** to **~/Desktop/local_repository**
and
```
cd ~/Desktop/local_repository/archives
```
```
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```

---

### Post by stinkeye on 2011-02-27
Douuble post.

---

### Post by utkarshjadhav on 2011-03-03
@stinkeye 
it solved the problem.
Thanks man!

---

