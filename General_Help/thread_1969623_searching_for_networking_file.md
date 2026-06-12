---
title: "searching for networking file"
date: 2012-04-30
forum: General Help
---

### Post by waldherrvonbirnbaum on 2012-04-30
Hi everybody!
Im searching for a file in ubuntu 11.10 with the content:
```

[global]
Name = PEAP_EXAMPLE
Description = PEAP network example

[service_peap]
Type = wifi
Name = eap
EAP = FAU-STAFF
CACertFile = /home/michel/.certs/cacert-telekom-root-ca-2.pem
Phase2 = MSCHAPV2
Identity = youridentity


```anyone knows, where to find it?
i want to to copy the values from my current connection to get a wpa2 enterprise internet on my meego machine.
Thank you!

---

### Post by codemaniac on 2012-04-30
Cannot you just grep specific text in all the files under your specific directory .
The below command line would find all the files containing the test "Description = PEAP network example" under $HOME.
```
grep -lir "Description = PEAP network example" ~
```

---

### Post by Habitual on 2012-04-30
Quite possibly in/under /etc/network/interfaces/*

```
sudo grep -iR "Description = PEAP network example" /etc/network/interfaces/* 
```

---

### Post by Miguel Tavares on 2012-05-01
a simple recursive find as follows:

find / -exec grep -il "PEAP_EXAMPLE" {} \; # This will give you the files that contain the grep search

find / -exec grep -i "PEAP_EXAMPLE" {} \; # This will give you the content without the filename for that grep search

Also you can manipulate the location to be searched recursively by changing the find / to find /bin or find /home, this because it will go recursive on /dev/ and /proc if you issue the above and will take some time.............

Kindest Regards
Miguel

---

