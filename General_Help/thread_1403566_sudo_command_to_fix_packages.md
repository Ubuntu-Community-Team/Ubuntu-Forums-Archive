---
title: "sudo command to fix packages"
date: 2010-02-10
forum: General Help
---

### Post by colobix on 2010-02-10
Hey. I got one of these broken packages message but can't remember the command to fix broken packages from the terminal.

Please help.

---

### Post by aviramof on 2010-02-10
you mean this?
[http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/](http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/)

---

### Post by Mustache Villain on 2010-02-10
Are you looking for **sudo apt-get -f install** ?

---

### Post by patchwork on 2010-02-10
or ```
sudo dpkg --configure -a
```

---

### Post by colobix on 2010-02-10
dont think so. I donno what that command does.
NO, I got the dpkg error thing

---

### Post by slakkie on 2010-02-10
You can use apt-get -f install.

You can also do something like this:

[http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/](http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/)

```

check_fix_pkg() {

    # Create the initial sudo call since we will use output from other sudo
    # command which might capture the password thingy
    sudo echo ""
    # This might take a while..
    RES=$(sudo debsums -c 2>&1)
    missing=$(echo -e "$RES" | grep  "missing")

    pkgs=$(echo -e "$missing" | awk '{NF=NF-1} {print $NF}' | sort -u)

    # Install the packages missing files
    sudo aptitude install $pkgs

    # Missing files
    mf=$(echo -e "$missing" | wc -l)
    # Packages missing files
    mfp=$(echo -e "$pkgs" | wc -l)

    echo "Missing files $mf, from $mfp packages"
}

```

Put that code in your .bashrc, source it and run check_fix_pkg

---

### Post by colobix on 2010-02-10
AH bingo. thanks alot sir :)

---

