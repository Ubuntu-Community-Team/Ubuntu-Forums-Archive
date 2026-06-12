---
title: "Evolution or Thunderbird...."
date: 2010-03-11
forum: General Help
---

### Post by pcura on 2010-03-11
[SIZE=3]Hello All,


I'm trying to add the PGP public key for the new repository. Here are the two lines I want to add for my e-mail but  don't know where to add on the new repository.

[/SIZE][SIZE=3]*$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)*[/SIZE]
 [SIZE=3]*$ sudo apt-key add tskariah.gpg*[/SIZE]
[SIZE=3]

I went to to the Synaptic Manager but could not find or where to place it. Would I create a new repository? 

Thanks in advance[/SIZE]

---

### Post by uRock on 2010-03-11
open a terminal via applications menu and paste the commands one at a time.

```
wget http://tskariah.000webhost.com/t_skariah.asc.gpg
```
```
sudo apt-key add tskariah.gpg
```

---

### Post by pcura on 2010-03-11
I tried putting it in the terminal but once i place the second line: 

this is what its saying

gpg: can't open `tskariah.gpg': No such file or directory

---

### Post by uRock on 2010-03-11
[s]WHere did you find those inputs? There must be something missing from that line.[/s] Read next post.

---

### Post by uRock on 2010-03-11
There is an underscore missing. Try this ```
sudo apt-key add t_skariah.gpg
```

---

### Post by pcura on 2010-03-11
Heres the link:

[http://sanaulla.wordpress.com/2008/02/17/free-pop3-and-smtp-access-to-yahoo-mail-using-ypops-in-ubuntu/](http://sanaulla.wordpress.com/2008/02/17/free-pop3-and-smtp-access-to-yahoo-mail-using-ypops-in-ubuntu/)

I'm setting my yahoo mail thru evolution. Some website say there is a backdoor access for yahoo mai. this is the only thing the is stopping me from continuing my configuration

---

### Post by uRock on 2010-03-11
Same stuff can be found here. [http://www.ubuntugeek.com/free-pop3-and-smtp-access-to-yahoo-mail-using-ypops-in-ubuntu.html](http://www.ubuntugeek.com/free-pop3-and-smtp-access-to-yahoo-mail-using-ypops-in-ubuntu.html)
```
sudo apt-key add t_skariah.gpg
```

---

### Post by pcura on 2010-03-11
same thing happen no such file.

---

### Post by DeMus on 2010-03-11
> **iRock said:**
> open a terminal via applications menu and paste the commands one at a time.

```
wget http://tskariah.000webhost.com/t_skariah.asc.gpg
```
```
sudo apt-key add tskariah.gpg
```

Type:
```
wget http://tskariah.000webhost.com/t_skariah.asc.gpg
```
```
sudo apt-key add t_skariah.asc.gpg
```

Did you also add the repository itself? This is only the key to release the use of it.

---

### Post by uRock on 2010-03-11
First you need to go to System> Administration> Software Sources and click on the Other Software tab, then click the Add button and copy and paste this line into the box ```
deb http://tskariah.000webhost.com/ubuntu ubuntu main
```
Then run the ```
sudo apt-key add t_skariah.gpg
```

Let me know what happens.
> **DeMus said:**
> Did you also add the repository itself? This is only the key to release the use of it.
I had just noticed that might be the case when looking at the ubuntugeek site.

---

### Post by uRock on 2010-03-11
```
deb http://tskariah.000webhost.com/ubuntu ubuntu main
```

---

### Post by pcura on 2010-03-11
I tried adding that to the apt line but the add source won't activate......its still grayed out. only cancel button is active.

---

### Post by uRock on 2010-03-11
> **pcura said:**
> I tried adding that to the apt line but the add source won't activate......its still grayed out. only cancel button is active.

I had to fix the line to add to the sources, sorry. The first addition I gave you was missing deb at the beginning.

---

### Post by uRock on 2010-03-11
I think I have been confusing us both. Can you tell me what has worked and what hasn't?

---

### Post by pcura on 2010-03-11
nothing works....

---

### Post by uRock on 2010-03-12
I just tried each step. First I added the entry to the software sources. That went fine.```
deb http://tskariah.000webhost.com/ubuntu ubuntu main
```

Second I added this line into the term, ```
wget http://tskariah.000webhost.com/t_skariah.asc.gpg
``` and that went fine, but,

When I entered the last command, it did not work. The only thing I can think of is that gpg server is not up.

---

### Post by pcura on 2010-03-12
I guess were back to square one.....lol if you read the thread from the beginning i stated that its telling me on the terminal that no such file.

---

### Post by uRock on 2010-03-12
> **pcura said:**
> I guess were back to square one.....lol if you read the thread from the beginning i stated that its telling me on the terminal that no such file.

The third command neither, sudo apt-key add t_skariah.gpg nor sudo apt-key add tskariah.gpg, work. You'd have to find a site that has that command in the correct context to try anything else.

---

### Post by uRock on 2010-03-12
If someone can post how to put this key in the correct format you can use the Authentication tab in the Software Sources app to add it. ```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

mQGiBEcFAqsRBACISwAo2EfAMtCPZGNBXksqF59hGzoNN7Z0lF vZTI6mQ+5GFyNC
alXe2O155IQ7O1NZ+K+Wa4O2z06rU3liNSn/H1sTB5iQAf/BYKxbxP/vFQvPnSi3
V9ZRYIT3Qky68pkFhiMzWILwXABa6oCHW/SxttpwFOpQvN38bWqwHouQbwCgkJAm
wBY2WO6Kd9PVcoS/VUj43rED/2D7Nrqiewyh6OFv2bUeTl6CyvdNg5t5QrM2l/Rm
dBOnUrB1Y6vQPveO1CiTk7AAjrjUhxOk86Ghezl/ob+zQ40JaCf0RIVOu9Gocv1r
vAKtqo0EY1w94XWL7u4aUYQ7jR1S6PMTmw36Xv9uUdjsbWXIsF aB0TT0+J8qNnAi
ZIWaA/499XnolDAJBfFjkAN0ZaTA6lOY3ElLMLmXadJ5LKZGjUPNYyHG GtSERRAT
xRc8YACmN+89dMfJgePTx+97F6E38gX3WgiBwb0dnch7aBLH1a U+yMWJYvSnxBzi
DuacUESnQ5y7qGPBCda7cu35BiCdfG6dIHrPYVf5FKIKbedcor QkVGhvbWFzIFNr
YXJpYWggPHRfc2thcmlhaEB5YWhvby5jb20+iGYEExECACYFAk cFAqsCGwMFCQHh
M4AGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRC15zMI4izzi/BBAJ9QI+Td5iYq
YiMwCdBKU/p6AkJtNwCggZek6u5XPxZF68fuoNADIEOtUWG5BA0ERwUDnRAQ AOTU
gTZ33Du/+YtPrFVNcuSmau3Kj/K94Rn1j34WRzeHnttlrXwZOHqe8TVyXT++f36I
whPhQv9AIsQTK/m15rUHTz0rWmDR0vrtI+lc4afnelX4KX589UfmWwiC+XIirgo0
uAaJ+giQU9L0Ct/IgV7rYsdpTj3R8FUxLU4nCoJDaDPi1YjGXrjZpr4TRZvn1kQo
e08DvuWPl/DTewp8OqTQ46lh0gaDBC1oU1zjXhgQlL44WofxcoukCyHKqHvY nEqR
sms9OTzlk8sbyYXFycjRWfup/XZjHKoI3JIvbX5OR+mOzEhYg5C2AwPgP3kQ5aFE
etWG12UWl7BwS6rMmaY+VHQVIt45TmEMHQSyfKC7YBp5BKqp0O pztSxE0h2sva6O
BX4YoWX4I81MvJDH/urGBSZi7HmagM/ymIM/sRkj6HjOgcNVdVFV8FkNA7Q3H6En
V+vP7e6S0hQroX8djQJ7XO5CgTMcaQt2888a+iHQM8IZoaupo6 mqJMlVO+IegObu
U50Lr8XwTyBu0v6x7LEzEaTAEsD25RHpoQuOlZd33slYqrxWzw t0hqNdn0WLE45K
Ndhpeq/Pw4DX+WcNuispnuNRGGQxDBvavTjK1aumSmZsUNdjZSRObZXYy fPAUGwt
i4/0ZTkOxw+9Vv/D5Vp27ZYl4lrBV1Kfhps2lrGbAAMFD/9f9v5dyvS7GAPePj44
XlS4JCJbtUkdYz2E+dO1K3O/fdKjiKow9yIu74E4yqGiK+0tiBSEFedqT9fuBZaO
b3lnm16TdG5bBQRb7q9zJSUpyfEc6b+w/OU4soWLh54tnkHCIElwqDL4mYr9FIob
MfYVZ6ddiEs+VSqOtCudxNa/DCRe3XbSsAzTvyuc1UlYw+NfUwciDwFhl1ow4CCP
NUl10Tyq2dVTCZ0yQaS24LryYRSw7rfa1gwkEV6WhD97FCqem2 tJS27Dc1VkRUTa
n5bv2D9VjWb+QGikGYCvYOYwwQB4c53zlGswIlcy/eRSmvmp/YCwPKT8N9eZMUM1
uQup06sj2Vj44l+87QUjRq5RId5cQnTEThb4CHieUkgoey3lRx AjKD2S3lr0XzME
1yLBo3olCQMqlESF05zks6HPVc2Ngn4XKcNzPM6oPIsMGBJmqZ wBjwQ1/5cgHMsr
Q8DYCJcjZ65II2VYxFjcs5oZZi2/EPp2Fl1c1zOVPMnw/nbGZIHvwsJSx1KGcEQ7
HnSGRKnNY/jppK8YVJtMAxtUysQqTCXCVqlgfuWDAMjikHDDdOuRAj6dUoyM u/nn
E6u3CllIwjAGdFp/vRqlBbKMRjgiUKc0OxnF0ifZBJ1WyYqFqAkHvy7TTea3+J+y
Es736ZYHOE3mrpSGGduT8K1esohPBBgRAgAPBQJHBQOdAhsMBQ kB4TOAAAoJELXn
MwjiLPOLfQAAn1ryWy1xP7U0mpeinaNVaymdKmrnAJwLuFy4rf 4V5lNDh74z7bgv
z9Hqdg==
=u8Q+
-----END PGP PUBLIC KEY BLOCK-----
```

---

### Post by DeMus on 2010-03-12
Copy all the text you have here and paste it in a new text file which you opened with Menu Applications - Accessories - Text editor. Then save the file on your desktop as **key.gpg**.
Now you can perform the following lines:

```
Open a terminal
```
```
cd Desktop
```
```
sudo apt-key add **key.gpg**
```

---

### Post by pcura on 2010-03-12
would notepad work though on this one?

---

### Post by DeMus on 2010-03-12
> **pcura said:**
> would notepad work though on this one?

Yes, it also creates a simple text file

---

### Post by uRock on 2010-03-12
> **DeMus said:**
> Copy all the text you have here and paste it in a new text file which you opened with Menu Applications - Accessories - Text editor. Then save the file on your desktop as **key.gpg**.
Now you can perform the following lines:

```
Open a terminal
```
```
cd Desktop
```
```
sudo apt-key add **key.gpg**
```

You are awesome, I hope it works for the OP, that is all they have listed on the site and the command to retrieve the key doesn't appear to work. Being that the wget command did something means the server has to be functioning.

---

### Post by DeMus on 2010-03-12
> **iRock said:**
> You are awesome, I hope it works for the OP, that is all they have listed on the site and the command to retrieve the key doesn't appear to work. Being that the wget command did something means the server has to be functioning.

When you read the original posting you see something goes wrong there.

$ wget [http://tskariah.000webhost.com/](http://tskariah.000webhost.com/)**t_skariah.asc.gpg**
$ sudo apt-key add **tskariah.gpg**

A file named t_skariah.asc.gpg is downloaded, but a file named tskariah.gpg is added. These are 2 different files. I pointed that out in my first post also. But doing it the way using the text editor also works, I do that all the time like this.

---

### Post by uRock on 2010-03-12
> **DeMus said:**
> When you read the original posting you see something goes wrong there.

$ wget [http://tskariah.000webhost.com/](http://tskariah.000webhost.com/)**t_skariah.asc.gpg**
$ sudo apt-key add **tskariah.gpg**

A file named t_skariah.asc.gpg is downloaded, but a file named tskariah.gpg is added. These are 2 different files. I pointed that out in my first post also. But doing it the way using the text editor also works, I do that all the time like this.

You sure did. I didn't even notice the change. Thanks for stepping in.

---

### Post by pcura on 2010-03-12
sorry totally newbie here.....i already saved the text file as key.gpg but i could not got to the desktop over the terminal....i typed cd desktop on the terminal.......it says no such file or directory

---

### Post by uRock on 2010-03-12
move the file to your home folder

---

### Post by pcura on 2010-03-12
i give up........lol. now this is what its telling me

gpg: no valid OpenPGP data found.

---

### Post by uRock on 2010-03-12
Did you try running this command that DeMus posted earlier? ```
sudo apt-key add t_skariah.asc.gpg
```

---

### Post by pcura on 2010-03-12
yes and this is what its saying on my terminal:

[sudo] password for pcura: 
gpg: can't open `t_skariah.asc.gpg': No such file or directory

Also, I came across this archived thread on ubuntu:

[http://ubuntuforums.org/archive/index.php/t-1155126.html](http://ubuntuforums.org/archive/index.php/t-1155126.html)

they're saying its a bad file and bad source

---

### Post by DeMus on 2010-03-12
> **pcura said:**
> sorry totally newbie here.....i already saved the text file as key.gpg but i could not got to the desktop over the terminal....i typed cd desktop on the terminal.......it says no such file or directory




[SIZE="3"]It is _D_esktop not _d_esktop. The _capital D_ is important otherwise Linux does not recognize the Desktop folder.[/SIZE]

---

