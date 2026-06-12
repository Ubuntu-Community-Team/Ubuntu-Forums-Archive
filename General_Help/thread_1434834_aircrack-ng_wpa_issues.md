---
title: "aircrack-ng wpa issues"
date: 2010-03-20
forum: General Help
---

### Post by neogeo124 on 2010-03-20
ok so I'm having issues with aircrack-ng, whenever I try to crack any capture file with wpa info it always says 


damian@damian-laptop:~$ sudo aircrack-ng /home/damian/wpa.full.cap
Opening /home/damian/wpa.full.cap
Read 15 packets.

   #  BSSID              ESSID                     Encryption

   1  00:14:6C:7E:40:80  teddy                     WPA (1 handshake)

Choosing first network as target.

Opening /home/damian/wpa.full.cap
Please specify a dictionary (option -w).


Quitting aircrack-ng...


any help would be appreciated

---

### Post by neogeo124 on 2010-03-20
bump

---

### Post by Helkaluin on 2010-03-20
> **neogeo124 said:**
> 
Please specify a dictionary (option -w).

Which, obviously, means that it is trying out a dictionary style attack and [double entendre]you need a dictionary[/double entendre].

By Reading The Fantastic Manual we find that, under the entry of the '-w' option, there's a link of suggested dictionaries: [http://www.aircrack-ng.org/doku.php?id=faq#where_can_i_find_good_wordlists](http://www.aircrack-ng.org/doku.php?id=faq#where_can_i_find_good_wordlists)

And really, do we support people trying to crack WPA who don't bother to read manuals here?...

---

### Post by neogeo124 on 2010-03-20
sorry, I'm still fairly new to ubuntu.. so what command would I type to make it use the dictionary?

---

### Post by hansdown on 2010-03-20
And really, do we support people trying to crack WPA who don't bother to read manuals here?...

Perhaps, we should.

Try decrypting this: 0ba0f049303e365494e4aea0f0102a0c

Hint: You'll need to de-hash, rotate, and know Latin. 
    	

You Da bomb.

---

### Post by Helkaluin on 2010-03-21
When you have all the information (the input for a program) but you don't know how to piece them into it (the syntax of the command), it is always useful to first try typing <command --help> in the terminal, thus:
```
aircrack-ng --help
```
gives us that:
```
usage: aircrack-ng [options] <.cap / .ivs file(s)>
...
-w <words> : path to wordlist(s) filename(s)
```
which means that, assuming a dictionary file with path <~/dict> and a cap file with path <~/dump.cap>, the input should be:
```
aircrack-ng -w ~/dict ~/dump.cap
```

> You Da bomb.
<literally>I'm not a terrorist!</literally>

---

### Post by lepel on 2010-05-01
I'm trying to understand the entire method of cracking a wireless network using aircrack.
I thought the idea is to collect a lot of encrypted packets, and then try to crack these using the fact that the IV's used to encrypt a packet are not always different from each other.
Right?
So what then is the point of using a dictionary? If you use that, why would you bother collecting packets? Using a dictionary is basically guessing the encryption-key isn't it?

---

### Post by haqim on 2010-05-28
i have problem...
wen i crak...(please specify a dictionary as target)
who can help me?
and who from malaysia?
plz!!!!

---

### Post by StephenF on 2010-05-28
> **lepel said:**
> I'm trying to understand the entire method of cracking a wireless network using aircrack.
I thought the idea is to collect a lot of encrypted packets, and then try to crack these using the fact that the IV's used to encrypt a packet are not always different from each other.
Right?
So what then is the point of using a dictionary? If you use that, why would you bother collecting packets? Using a dictionary is basically guessing the encryption-key isn't it?
Yes it is and it's the only known technique for cracking WPA. WEP keys can be cracked with a large enough supply of IVs.

---

### Post by haqim on 2010-05-28
who can help me?
what i can do?
any bdy can help me?
who from malaysia,indonesia,singapore?

---

