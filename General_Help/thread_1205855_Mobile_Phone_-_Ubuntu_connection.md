---
title: "Mobile Phone - Ubuntu connection"
date: 2009-07-06
forum: General Help
---

### Post by yildiz.a on 2009-07-06
Hi,

I have a mobile called ANYCOOL T838i which is made in Chinese, 

as you can guess, there is no enough support for PC. I wonder 

that: When I connect my phone to x86 PC installed Ubuntu, I cannot 

see any change from GUI or command line. Anyone knows how I could 

afford it, so I mean: How can I see files in my mobile? Thanks...

Note: I tried also ls /dev or other commands but I think it is about driver problem?

---

### Post by philinux on 2009-07-06
With the phone plugged in open a terminal. Apps>Accessories>terminal.

Use this command and paste back the result.

```
lsusb
```

---

### Post by yildiz.a on 2009-07-06
> **philinux said:**
> With the phone plugged in open a terminal. Apps>Accessories>terminal.

Use this command and paste back the result.

```
lsusb
```

I wrote "lsusb":

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by blueridgedog on 2009-07-06
Was the phone on when you issued lsusb?

---

### Post by yildiz.a on 2009-07-07
> **blueridgedog said:**
> Was the phone on when you issued lsusb?

Yes, it was. As you see, there is no change on USB between phone 

connected or not.

---

### Post by binbash on 2009-07-07
Hmm after seeing lsusb output, it is better to connect it via bluetooth instead of USB : )

---

### Post by elliotn on 2009-07-07
Yes its better with bluetooth

---

### Post by yildiz.a on 2009-07-07
> **binbash said:**
> Hmm after seeing lsusb output, it is better to connect it via bluetooth instead of USB : )


Yes, I know that. But I want it to use to see files inside on it or format

it.

---

