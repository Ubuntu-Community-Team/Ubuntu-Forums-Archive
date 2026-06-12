---
title: "Updating Filezilla to 3.3.2"
date: 2010-03-19
forum: General Help
---

### Post by Almeida1 on 2010-03-19
Ive just insalled Ubuntu 9.10 and installed Filezilla from the Ubuntu Software Centre, however this is only version 3.2.7.2. 

How do I update this to 3.3.2? 

Ive downloaded the tar.bz2 file and extracted it in Downloads but how I do install it from here?

---

### Post by n0dix on 2010-03-19
Extract the tar.bz2 and read the README file. Maybe you get and error with the old version 3.2.7.2.

---

### Post by Almeida1 on 2010-03-19
> **n0dix said:**
> Extract the tar.bz2 and read the README file. Maybe you get and error with the old version 3.2.7.2.

I have read the INSTALL file and it says to do the following:

mkdir compile
cd compile
../configure
make
make install

However, after I do ../configure I get the following error:

```

configure: error:
            wxWidgets must be installed on your system
        but either the wx-config script couldn't be found or
        no compatible wxWidgets configuration has been insalled.

        Compatible wxWidgets configurations are the unicode builds
        of wxGTK, wxMac and wxMSW.

        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets version is 2.8.9 or above.

```

How do I install wxWidgets? Ive been looking round but cant seem to find an answer.

Cheers

---

### Post by n0dix on 2010-03-19
Yes.

---

### Post by Almeida1 on 2010-03-19
> **n0dix said:**
> Yes.

:confused:

---

### Post by n0dix on 2010-03-19
> **Almeida1 said:**
> :confused:

install the package.

---

### Post by sandyd on 2010-03-19
> **Almeida1 said:**
> Ive just insalled Ubuntu 9.10 and installed Filezilla from the Ubuntu Software Centre, however this is only version 3.2.7.2. 

How do I update this to 3.3.2? 

Ive downloaded the tar.bz2 file and extracted it in Downloads but how I do install it from here?
```

cd ~/Downloads
wget -c http://d10xg45o6p6dbl.cloudfront.net/projects/f/filezilla/FileZilla_3.3.2_i586-linux-gnu.tar.bz2
bunzip2 -d FileZilla_3.3.2_i586-linux-gnu.tar.bz2
tar xvf FileZilla_3.3.2_i586-linux-gnu.tar
sudo mv FileZilla3 /opt
cd /opt/FileZilla3
sudo dpkg-divert --divert /usr/bin/filezilla --rename /usr/bin/filezilla.bak
sudo dpkg-divert --divert /usr/bin/fzsftp --rename /usr/bin/fzsftp.bak
sudo dpkg-divert --divert /usr/bin/fzputtygen --rename /usr/bin/fzputtygen.bak
sudo rm /usr/bin/filezilla
sudo rm /usr/bin/fzsftp
sudo rm /usr/bin/fzputtygen
sudo ln /opt/FileZilla3/bin/filezilla /usr/bin/filezilla
sudo ln /opt/FileZilla3/bin/fzsftp /usr/bin/fzsftp
sudo ln /opt/FileZilla3/bin/fzputtygen /usr/bin/fzputtygen
```

---

### Post by Almeida1 on 2010-03-19
> **carlee said:**
> ```

cd ~/Downloads
wget -c http://d10xg45o6p6dbl.cloudfront.net/projects/f/filezilla/FileZilla_3.3.2_i586-linux-gnu.tar.bz2
bunzip2 -d FileZilla_3.3.2_i586-linux-gnu.tar.bz2
tar xvf FileZilla_3.3.2_i586-linux-gnu.tar
sudo mv FileZilla3 /opt
cd /opt/FileZilla3
sudo dpkg-divert --divert /usr/bin/filezilla --rename /usr/bin/filezilla.bak
sudo dpkg-divert --divert /usr/bin/fzsftp --rename /usr/bin/fzsftp.bak
sudo dpkg-divert --divert /usr/bin/fzputtygen --rename /usr/bin/fzputtygen.bak
sudo ln /opt/FileZilla3/bin/filezilla /usr/bin/filezilla
sudo ln /opt/FileZilla3/bin/fzsftp /usr/bin/fzsftp
sudo ln /opt/FileZilla3/bin/fzputtygen /usr/bin/fzputtygen
```

Thanks for the great reply. Everything seemed to be going smoothly but the last three gave a message saying File Exists. So now what?! Sorry I am new to linux so appreciate your help!

---

### Post by Almeida1 on 2010-03-19
I have done it now by running filezilla using ./Filezilla from within /opt/filezilla/bin/ 

I assume I have to remove the old filezilla thats why it was saying file exists. Ill try that now.

---

### Post by sandyd on 2010-03-19
> **Almeida1 said:**
> I have done it now by running filezilla using ./Filezilla from within /opt/filezilla/bin/ 

I assume I have to remove the old filezilla thats why it was saying file exists. Ill try that now.
fixed ;)

p.s. since filezilla supports automatic upgrade, you might want to 
```

sudo chmod -R 777 /opt/FileZilla3

```
That will make the /opt/FileZilla3 writable for all users.
Since it is writable for all users, you can simply click the "upgrade" button when filezilla notifies you of a new release.

If you dont want to do that, to install updates when filezilla notifies you of them, run filezilla with
```

gksudo filezilla
```

---

### Post by AnotherNoob on 2010-04-01
@ Carlee i use your steps but now its not load toolbar 

any one know proper steps ?

---

