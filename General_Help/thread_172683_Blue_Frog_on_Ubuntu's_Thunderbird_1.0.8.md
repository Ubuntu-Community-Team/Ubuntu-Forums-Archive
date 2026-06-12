---
title: "Blue Frog on Ubuntu's Thunderbird 1.0.8"
date: 2006-05-09
forum: General Help
---

### Post by anb on 2006-05-09
Hello

Does anyone use the Blue Frog extension on Thunderbird 1.0.8 (Ubuntu's build?). I've installed the 0.15 version and everytime i launch Thunderbird it says "This item will be uninstalled after you restart Thunderbird". When I've installed the 0.16, it's just the same (and it still shows it's 0.15).

When I run it from the console, I get such messages:

```
# mozilla-thunderbird
selected locale: en-US
 ***** Registering: Clean Compreg! ****
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 250 --> -1 THRESHOLD: 8 --> -1 *** loading the extensions datasource
*** nsExtensionManager::_finishOperations - failure, catching exception so finalize window can close [Exception... "Cannot modify properties of a WrappedNative"  nsresult: "0x80570034 (NS_ERROR_XPC_CANT_MODIFY_PROP_ON_WN)"  location: "JS frame :: file:///usr/lib/mozilla-thunderbird/components/nsExtensionManager.js :: nsExtensionInstaller_install :: line 964"  data: no]
```

Does anyone know what's going on? ;-)

---

### Post by kaveraj on 2006-05-10
I use bluefrog on my gmail account with firefox plugin. I think that the bluefrog program must be installed apart from the plugins. You can download the program from [http://members.bluesecurity.com/cwa/download.do](http://members.bluesecurity.com/cwa/download.do)

I tried compiling the source. It downloaded the dependencies and compiled. But when I compiled the main buildfrog.sh I got  the following error

> ./crypto_utils.cpp: In static member function 'static bool CryptoUtils::is_buffer_authentic_sha256(const char*, int, const char*)':
./crypto_utils.cpp:116: error: 'SHA256_DIGEST_LENGTH' was not declared in this scope
./crypto_utils.cpp:116: error: 'md' was not declared in this scope
./crypto_utils.cpp:116: error: 'SHA256' was not declared in this scope
make[1]: *** [crypto_utils.o] Error 1


Then I downloaded the rpm package, converted it to deb using alien and installed it. The program runs and successfully logged me in. But beyond that I am not sure whether it is working. Till this works I will continue to submit opt outs from windows.

Will be great if someone found a way to work this out.

---

### Post by towner on 2006-05-10
Hi All

I've got bluefrog installed now for use on my gmail account, using the same method as kaveraj (and I have the same problem as kaveraj too ;) 

I've used the windows version at work with success. 

I'm not happy with the linux version though. I've mailed the developers and will post any reply received.

---

### Post by wblancqu on 2006-05-11
I use blue frog. Just downloaded the binary. This might be a stupid question but it seems to run, but there is no icon in tray like in windows, is this normal? I made it sit in tray using alltray.

---

### Post by kaveraj on 2006-05-12
which binary is that. can you give the link and the steps you followed. 

Meanwhile the bluesecurity website seems to be down. Another DDOS attack?? If it is then it is very bad. Moreover is this method working for you. My spam seems to have increased upto 10 fold due to the stepped up counter attack of the spammers. 

But I am not going to give it up yet. If these sick spamming a$$es could have the strength to stand up , then it would be a shame to not stand up against them. :twisted:

---

### Post by wblancqu on 2006-05-12
How-to is coming...

---

### Post by wblancqu on 2006-05-15
Howto is [HERE]("http://ubuntuforums.org/showthread.php?t=176192").

---

