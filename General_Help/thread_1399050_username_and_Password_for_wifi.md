---
title: "username and Password for wifi"
date: 2010-02-05
forum: General Help
---

### Post by Vishnu V on 2010-02-05
Hai
In our college the wifi has  username and password.I can access internet through browser but when i try to update my system or download any package through Synaptic package manager or ubuntu software center, it shows an error. I think it is due to lack of username and password. How can i enter the username and password for Network in ubuntu (not for browser).


Sorry for my bad English

Thanks

---

### Post by warfacegod on 2010-02-05
What errors are being shown?

---

### Post by anaconda on 2010-02-05
could it be that your school restricts the internet pages you can access, and ubuntu repositories are not on the allowed list??

As far as I understand, if you have a internet connection, then all apps that need it have the connection

---

### Post by warfacegod on 2010-02-05
That was my understanding as well.

---

### Post by Vishnu V on 2010-02-05
> **anaconda said:**
> could it be that your school restricts the internet pages you can access, and ubuntu repositories are not on the allowed list??

As far as I understand, if you have a internet connection, then all apps that need it have the connection

I don't think that school restricts ubuntu repositories because  i can  download  packages directly typing the url in the web browser

---

### Post by Vishnu V on 2010-02-05
> **warfacegod said:**
> What errors are being shown?

Sorry i don't have the error with me now. I will post it tomorrow

---

### Post by Vishnu V on 2010-02-08
This is the error i got when i tried to install 3ddesktop from synaptic package manager.
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-5.1ubuntu1_i386.deb
  407  Proxy Authentication Required
[code]
but i can directly download package via 
[code]
http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-5.1ubuntu1_i386.deb

```

---

### Post by megamania on 2010-02-08
> **Vishnu V said:**
> Hai
In our college the wifi has  username and password.
Do you mean you have to authenticate through the browser before being able to access websites?

In that case, you may need to authenticate on the web browser also before trying to download packages with apt. So, open your browser, login, leave it open (just in case) and then try running apt (the synaptic package manager).

---

### Post by crlang13 on 2010-02-08
What are your system wide proxy settings?  I have to run through a proxy server to surf the web at my college.  Go to system > preferences > network proxy.  Configure your school's proxy server in there and apply system wide.

It's worked for me...

---

### Post by warfacegod on 2010-02-08
> **Vishnu V said:**
> This is the error i got when i tried to install 3ddesktop from synaptic package manager.
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-5.1ubuntu1_i386.deb
  407  Proxy Authentication Required
[code]
but i can directly download package via 
[code]
http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-5.1ubuntu1_i386.deb

```

Have you tried a mirror site?

---

### Post by crlang13 on 2010-02-08
> **crlang13 said:**
> What are your system wide proxy settings?  I have to run through a proxy server to surf the web at my college.  Go to system > preferences > network proxy.  Configure your school's proxy server in there and apply system wide.

It's worked for me...

Now it's not working... I changed a whole lot of things up and now it won't work... HOWEVER, you can manually configure your network proxy in the synaptic package manager > settings > preferences > network.

give that a try for now i guess.  sorry for the bad advice earlier.

---

### Post by Vishnu V on 2010-02-09
> **megamania said:**
> Do you mean you have to authenticate through the browser before being able to access websites?

In that case, you may need to authenticate on the web browser also before trying to download packages with apt. So, open your browser, login, leave it open (just in case) and then try running apt (the synaptic package manager).

This is what i am searching for 
Thank You very much

---

### Post by megamania on 2010-02-09
> **Vishnu V said:**
> This is what i am searching for 
Thank You very much
Glad I could help!

---

### Post by AmnesiA05 on 2010-11-04
my school also has a username and password for its wifi... 
i have tried the suggestions here but no luck...
the error message says
[HTML]Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]
i hope some one could help me....
Thanks in advance:guitar:

---

