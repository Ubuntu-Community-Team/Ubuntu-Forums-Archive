---
title: "How to change APT's cache directory"
date: 2006-03-15
forum: General Help
---

### Post by piggysmile on 2006-03-15
How can APT's default cache location (/var/cache/apt/archives) be change to somewhere else?

---

### Post by kevinlyfellow on 2007-08-02
I know this is old, but I'd like to do that also.  I've found that there may be a way to configure apt.conf but there is no apt.conf by default in ubuntu or debian etch.  Does anyone have a clue on this.  I've looked around and the only answer I can find is "you don't need to".  Please don't respond with the same, since it is not productive.

---

### Post by capink on 2007-08-02
To change the cache permanently do the following:

1. create the directiory that you want as the new cache. within it create a subdirectiory named partial. e.g if you want the cache to be in directory called cache in your home directory :

```
mkdir -p ~/cache/partial 
```

2. Add the following to the file apt.conf "if the file is not present create it" :

dir::cache::archives "/home/username/cache"

```

sudo -s
echo "dir::cache::archives \"/home/`whoami`/cache\";" >> /etc/apt/apt.conf
exit
```




If you want to change the cache temporarily you can do so at the command line:

```
sudo apt-get -o dir::cache::archives="/the/path/to/temporary/cache/" install packagename
```

Note: Make sure the cache contain a subdirectory called partial

---

### Post by kevinlyfellow on 2007-08-02
Excellent!!!  Thank you very much, I honestly didn't expect to get an answer.  :-)  You've made my day.  

It's a lot simpler than I thought it would be.  I looked at the example apt.conf and it looks like it is written in c.  The man pages hinted at your method, but the apt.conf syntax threw me off.

Thanks again.

---

### Post by chipwizme on 2008-05-14
Personally, I find that changing default paths is bad form, as it confuses administrators, broken programs, and you. I would recommend creating a symbolic link to your new cache directory (this will DELETE your old cache):

sudo rm -rf /var/cache/apt/archives
sudo ln -s /path/to/new/cache /var/cache/apt/archives

---

