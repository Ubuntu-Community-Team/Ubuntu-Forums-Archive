---
title: "Wpa_supplicant build fails. cannot find -lcrypto"
date: 2006-02-18
forum: General Help
---

### Post by racyrefinedraj on 2006-02-18
So I am installing ubuntu on my desktop (already running fine on my lappy :KS ) but I can't get wpa_supplicant to build. I have all the prerequisites installed including a the version of OpenSSL that their website says works. 

here's what I do (in the directory where I unpacked the source for wpa_supplicant:

```

sudo make clean
sudo make

```

Everything goes along fine until:

```
cc  -o wpa_passphrase wpa_passphrase.o sha1.o md5.o os_unix.o crypto.o -lcrypto
/usr/bin/ld: cannot find -lcrypto
collect2: ld returned 1 exit status
make: *** [wpa_passphrase] Error 1

```

I KNOW that this libcrypto library is installed. In fact, i can navigate to /usr/local/ssl/lib and LOOK at it! I've tried exporting the path to ldconfig and changing the lines in .config to point to the right path. but ARGH it still doesn't work. To add insult to injury, I followed the exact same process on my laptop and wpa_supplicant is working like a charm. 

any suggestions?

---

