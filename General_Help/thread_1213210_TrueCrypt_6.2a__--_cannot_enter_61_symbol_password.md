---
title: "TrueCrypt 6.2a  -- cannot enter 61 symbol password."
date: 2009-07-14
forum: General Help
---

### Post by ==Troy== on 2009-07-14
I am sorry to write here, but since the Truecrypt forums do not allow registration from "free" emails, and I never had provider's e-mail, I am hoping to possibly get some help here.


When encrypting a drive, TrueCrypt allows to enter 60-64 symbol passwords, but, on the other hand, when DE-cryption, it allows me only to enter about 54 symbols, and thats it. Hence even knowing the password, I CANNOT de-crypt it.


Any help will be greatly appreciated. I have several GB of data part of which I need for tomorrow's presentation...

Thank you.

---

### Post by michy99 on 2009-07-14
Have you tried mounting it from the command line?

---

### Post by ==Troy== on 2009-07-15
I have tried to launch it from  the terminal, but I cannot do it properly,


a simple example of echo "a !b" returns error
echo "a \!b" returns a \!b when I need a !b

when using the ' '. I cannot then do the 
echo 'a \'b'


any help would be appreciated.

---

### Post by michy99 on 2009-07-15
I guess you are having a problem with a space in the password. Try this to mount from the command line.```
sudo truecrypt -p 'PASSWORD' VOLUME MOUNTPOINT
```PASSWORD = your password - notice the quote marks ' will take care of spaces.

VOLUME = truecrypt volume

MOUNTPOINT = place to mount to (/media/truecrypt1 for example)

Note that this is not secure in that your password is exposed and saved in your command history. I would use this method only if it won't mount any other way.

---

### Post by ==Troy== on 2009-07-15
I am also having problem with the 'a 'b' case, since \' doesnt work either.

---

### Post by michy99 on 2009-07-15
Going back to the problem of the long password, I was able to enter a 64 character password by running from the terminal without the -p option and entering it in the dialog that popped up.```
sudo truecrypt VOLUME MOUNTPOINT
```

In fact, I just tested and it works from the truecrypt GUI also. Are you sure it doesn't work for you? What version of truecrypt do you have?

---

### Post by ==Troy== on 2009-07-15
I am using 6.2a and it just wont let me enter anything longer than 54-58 symbols. No matter where, GUI, or GUI ran from the terminal..

---

### Post by michy99 on 2009-07-15
I have 6.2 and it definitely accepts 64 character passwords. I assume you got 6.2a from the website. Maybe you should try installing 6.2 from the repository and see if it works.```
sudo apt-get install truecrypt
```If it does, then this is a bug in 6.2a and should be reported.

---

