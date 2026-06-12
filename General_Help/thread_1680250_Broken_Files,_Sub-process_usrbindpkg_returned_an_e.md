---
title: "Broken Files, Sub-process /usr/bin/dpkg returned an error code (100)"
date: 2011-02-02
forum: General Help
---

### Post by TheStelz on 2011-02-02
First off, I am very new to ubuntu. But whenever i try to run
sudo apt-get upgrade or install any new programs i get this message 


You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.7) but 2.11.1-0ubuntu7.8 is installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.11.1-0ubuntu7.7 is installed

so i run sudo apt-get -f install and get this message


Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

I've read that I might need to change the permissions of /usr/bin/dpkg but I have no idea how to do this. Help would be greatly appreciated

---

### Post by rickyrockrat on 2011-02-04
sudo chmod 755 /path/to/file

Use this to check the owner & permissions:
ls -l /path/to/file

---

### Post by TheStelz on 2011-02-11
i ran sudo chmod 755 /usr/bin/dpkg and i got the following output

chmod: cannot access `/usr/bin/dpkg': No such file or directory

---

