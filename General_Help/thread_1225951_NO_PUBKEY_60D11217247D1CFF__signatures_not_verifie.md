---
title: "NO_PUBKEY: 60D11217247D1CFF / signatures not verified the public key not available"
date: 2009-07-29
forum: General Help
---

### Post by GSpuhler on 2009-07-29
NO_PUBKEY: 60D11217247D1CFF
  signatures couldn't be verified because the public key is not available.
  

Hello.
I never had this problem before. Now in 9.04, I get this error message after I downloaded the new OpenOffice 3.1. It downloads all the package information iand then 

W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
 
 
  occurs. I am not able to handle this problem. Can somebody tell me what to do and how ?  Any help will be much appreciated. Thanks.

---

### Post by Zorael on 2009-07-29
Do you have the **medibuntu-keyring** package installed? It is supposed to take care of adding the needed Medibuntu authentication keys.

Alternatively you could add the key manually, I guess.
```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF
```

---

### Post by fragos on 2009-07-29
Had a similar problem:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

@Zorael's method worked for me when I substituted 0624A220 for the one in the example. My thanks to Zorael.

---

