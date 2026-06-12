---
title: "Test User password with Zenity/Bash script"
date: 2009-08-05
forum: General Help
---

### Post by Jose Catre-Vandis on 2009-08-05
I am working up a script, and what I need to do is test the entry made by a user into a zenity dialog against their password. If they enter the correct password (the one they logged in with) then the rest of the script will proceed.

How can I call up a user's password in a bash script. Is there a variable in bash to do this? I clearly do not want to have to put it in as plain text!

---

### Post by michy99 on 2009-08-05
The password is stored in /etc/shadow as a md5sum. You have to do a md5sum on the entry and compare it to the corresponding entry in /etc/shadow.

---

### Post by Jose Catre-Vandis on 2009-08-05
Makes sense, how do I run md5 against a word in order to get the hash?

EDIT: figured this out?
```
echo -n "password" | md5sum
```
but this looks nothing like the entry against the user in /etc/shadow (which is 2/3 times longer)?

---

### Post by michy99 on 2009-08-05
Here's a short explanation of /etc/shadow. Apparently it can use other encryptions besides md5.

[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

---

### Post by Jose Catre-Vandis on 2009-08-06
Hmmm still doesn't really help, is a different encryption being used - SHA-512, inidcated by the $6$?

Here is my /etc/shadow entry (a few digits changed to protect the innocent)
> jose:$6$gPC.6/BqBx$Ag0fumVhbVmpx5b5TCDe9vra868eSnNde7vqNeD9nWaCSEQuuirEYshHLMuJ7obKfueXsD3DSQ8jZoog.5BG81:14357:0:99999:7:::
and here is the output from "echo -n "password" | md5sum"
> 65ba469a2f5471be97ed178d5fba24d4  -
(again a few digits changed, but this is about size and type)

---

### Post by sisco311 on 2009-08-06
You can use sudo. Add the user in the sudoers file:
```
[COLOR="Blue"]username[/COLOR] ALL=([COLOR="Red"]username[/COLOR]) /path/to/script
```
[COLOR="Blue"]username[/COLOR] is allowed to run the /path/to/script script as user:[COLOR="Red"]username[/COLOR]

Then:
```
sudo -u username /path/to/script
```
will prompt for the user's password.

---

### Post by Jose Catre-Vandis on 2009-08-06
> **sisco311 said:**
> You can use sudo. Add the user in the sudoers file:
```
[COLOR="Blue"]username[/COLOR] ALL=([COLOR="Red"]username[/COLOR]) /path/to/script
```
[COLOR="Blue"]username[/COLOR] is allowed to run the /path/to/script script as user:[COLOR="Red"]username[/COLOR]

Then:
```
sudo -u username /path/to/script
```
will prompt for the user's password.

Thanks, I know, but trying to stay away from sudo, and this has now become a bit of a quest to see **how I can check a users password against that stored in the system**, so if the user doesn't know sudo, this is their authentication for the script to run.

Seems if I can find a way to encrypt a string using the right algorithm, which I believe to be SHA-512, I will be able to compare this with the contents of /etc/shadow, once I have figured out how to extract the key. :)

---

### Post by sisco311 on 2009-08-06
> **Jose Catre-Vandis said:**
> 

Seems if I can find a way to encrypt a string using the right algorithm, which I believe to be SHA-512, I will be able to compare this with the contents of /etc/shadow, once I have figured out how to extract the key. :)

```
mkpasswd -m sha-512 password saltsalt
```

But, You need root permissions to access the shadow file.

---

### Post by unutbu on 2009-08-06
Note the use of md5 encryption:
```

sudo useradd --create-home --user-group --password $(mkpasswd -s -m md5 pea) --comment "Sweat Pea" --shell /bin/bash pea

```
I checked that it works with
```

su pea
```
```

sudo userdel -r pea
```

This also works:
```

sudo useradd --create-home --user-group --password $(mkpasswd -s -m sha-512 pea) --comment "Sweat Pea" --shell /bin/bash pea
```

I don't know how many different types of encryption work. But I think this means you might have to check a user's unencrypted password by encrypting it in many (at least 2) different ways.

---

### Post by sisco311 on 2009-08-06
in the shadow file:
```
$[COLOR="Red"]6[/COLOR]$[COLOR="Blue"]NU7T6629[/COLOR]$eJuF3qoAmPBTr9keSxmfFZzgpfEyCsk7OmdGpRJ8Purl/nDwt69AhdOJbLdsW3QiSnfZzD8PNEQ2lBS3.7QJp/
```
[COLOR="Red"]6 is the encryption type[/COLOR]
```
              ID  | Method
              &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
              1   | MD5
              2a  | Blowfish (not in mainline glibc; added in some
                  | Linux distributions)
              5   | SHA-256 (since glibc 2.7)
              6   | SHA-512 (since glibc 2.7)


```
[COLOR="Blue"]and NU7T6629 is the salt[/COLOR]

---

### Post by Jose Catre-Vandis on 2009-08-06
OK, thanks guys, looks like you have all the answers, just that i don't understand how to use them! :)

Let's say I extract in advance the hash from the /etc/shadow file for use in my script (I'll just stick to a single user for now). I will need to compare the hash, with a hash generated by the script on the password entered.

So,

user = jose
pass = mypasswd
hash = eJuF3qoAmPBTr9keSxmfFZzgpfEyCsk7OmdGpRJ8Purl/nDwt69AhdOJbLdsW3QiSnfZzD8PNEQ2lBS3.7QJp/
(as per sisco311's post)

in plain english, the script would do the following:

1.  take the input from zenity and put into variable > $PASS
2.  take $PASS and 
**2.1 perform encryption on it to produce a hash > $TESTHASH**
3.  compare $TESTHASH with the extracted hash key from /etc/shadow $HASH
4.  perform rest of script if comparison succssful

I am OK with sorting out 1,2,3,4 it's **2.1** I don't know how to do

Thanks for all your help so far :)

---

### Post by sisco311 on 2009-08-06
```
mkpasswd -m sha-512 password NU7T6629
```
where password is the password entered by the user 
and NU7T6629 is the salt from /etc/shadow

---

### Post by Jose Catre-Vandis on 2009-08-06
Will this have any impact on the existing password?

---

### Post by unutbu on 2009-08-06
No, it just returns a string. For example,
```
mkpasswd -m sha-512 password NU7T6629NU7T6629
$6$NU7T6629NU7T6629$BaKyvMTWu.H0jiZELdCQrDTkNgljkx7rvyg7NoozLZszsrEtx5.SsWNE385xz4TgQ7RClBkeWTMiIgh6d4x1B1
```

[s](For sha-512, the salt has to be 16 bytes)[/s]
Edit: sha-512 can have variable salt lengths, but mkpasswd in pre-Ubuntu 9.10 does not support them. See [http://ubuntuforums.org/showpost.php?p=7348969&postcount=13](http://ubuntuforums.org/showpost.php?p=7348969&postcount=13)

---

### Post by sisco311 on 2009-08-06
never mind :)

---

### Post by Jose Catre-Vandis on 2009-08-06
Yes, this works, I tested it with a 16 character SALT, but my SALT is 10 characters and not 8 ??

```
hPC.6/DqBy
```

so I am not getting a matching hash as a result, and mypasswd complains about the wrong number of characters

EDIT:

I see there is a bug in mypasswd that cannot cope with variable length salts. Am I stuffed or is there another way?

---

### Post by sisco311 on 2009-08-06
```
python -c "import crypt, getpass, pwd; print crypt.crypt('password', '\$6\$[COLOR="Red"]SALT[/COLOR]\$')"
```

---

### Post by Jose Catre-Vandis on 2009-08-06
Yay - success :)

Many thanks for all your help :)

---

### Post by lswb on 2009-08-06
Make sure you save the other users password somewhere so you can impersonate them later!

---

