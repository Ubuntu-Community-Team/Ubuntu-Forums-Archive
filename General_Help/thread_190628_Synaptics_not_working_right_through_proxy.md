---
title: "Synaptics not working right through proxy"
date: 2006-06-06
forum: General Help
---

### Post by djcrash1981 on 2006-06-06
I upgraded from breezy to dapper from the alternate cd and since then my synaptic stopped work.
I'm behind a proxy and i been trying to configure synaptic in any possible way.

In the network tab in preferences i had put:
http proxy: {user}:{passwd}@proxy port 8080

When i'm trying to reload the list of software it send me this error:

[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:) 407 Proxy authorization required


The fun thing of this is that on my terminal window i put the variable:
export http_proxy=http://{user}:{passwd}@proxy:8080

And apt-get works normally, what is happening someone can point me out where i'm wrong? ](*,) 

Thanks in advance :D

---

### Post by mcwtlg on 2006-06-06
sudo nano /etc/apt/apt.conf

Acquire::http::Proxy "$address_of_proxy:Number_of_port";

I have not had any problems with this.

---

### Post by djcrash1981 on 2006-06-07
Ok, i'd done that and it still doesnt work at all, any ideas???? :confused:

---

### Post by mcwtlg on 2006-06-07
[QUOTE=djcrash1981]Ok, i'd done that and it still doesnt work at all, any ideas???? :confused:[/QUOTE]

Not at this time.

---

### Post by yellow beard on 2006-06-13
This is the same problem im having. Ive included my user name/password in apt.conf proxy address and in the proxy settings in gnome but its still saying i dont have permission when i try apt get. but it for some reason works when i use the export command.

---

### Post by yellow beard on 2006-06-14
Has anyone got any ideas how to fix this and get apt working through a login proxy server????

---

### Post by kokimunchter on 2006-06-17
i nailed this one recently, took me a lot of reading till i found the missing comment needed ;) . apparently, you just have to add %20 in the script:

Acquire {http:proxy**%20**"http://DOMAIN\user:passwd@proxy:port/";

mock script:

Acquire {http:proxy%20"http://UBUNTU-DOM\DapperDrake:p@$$w0rd:5658/";

i hope this helps :D

---

### Post by yellow beard on 2006-06-18
[QUOTE=kokimunchter]i nailed this one recently, took me a lot of reading till i found the missing comment needed ;) . apparently, you just have to add %20 in the script:

Acquire {http:proxy**%20**"http://DOMAIN\user:passwd@proxy:port/";

mock script:

Acquire {http:proxy%20"http://UBUNTU-DOM\DapperDrake:p@$$w0rd:5658/";

i hope this helps :D[/QUOTE]

so like this?
```
Acquire {http:proxy%20"usrname:password@192.168.0.1:8080/";
}
```

---

### Post by lauro.sa on 2006-06-19
**There are 2 ways:**

**1st. **Configure your synaptic (apt-get) proxy settings:

 a. Return your /etc/apt/apt.conf to the original:

*Acquire::http:Proxy "False";*

 b. In *Synaptic/Preferences/Network* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*
Proxy FTP:  *repeat*

 c. In *System/Preferences/Network Proxy* type:

*Direct Connection*

 With this, http_proxy variable will be blank and it will not confuse your Synaptic.

-------------------------------------------------------------

**2nd.** Configure your network proxy settings (http_proxy variable):

 a. Return your */etc/apt/apt.conf* to the original:

*Acquire::http:Proxy "False";*

 b. In *System/Preferences/Network Proxy* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*  DETAILS: *put user and passw again*
Proxy HTTPs:  *repeat*
Proxy FTP:  *repeat*
Host Socks:  *repeat*

 This works because the **http_proxy variable is mandatory **to Synaptic (apt-get).
 **[COLOR="Red"]The problem of this option is[/COLOR]**: with the command "echo $http_proxy" users can see your passw.

-------------------------------------------------------------

---

### Post by kokimunchter on 2006-06-19
yellowbeard,

your code:
Acquire {httproxy%20"http://DOMAIN\userasswd@proxyort/";

should read like this:

Acquire {http:proxy%20"http://domain\usrname:password@192.168.0.1:8080/";
}

..and don't forget to specify your domain
..after using the code i was able to update the necessary files i needed

---

### Post by ProBlazer on 2006-11-24
> There are 2 ways:

1st. Configure your synaptic (apt-get) proxy settings:

a. Return your /etc/apt/apt.conf to the original:

Acquire::http:Proxy "False";

b. In Synaptic/Preferences/Network type:

Manual Proxy:
Proxy HTTP: user:Passw@proxy PORT: port
Proxy FTP: repeat

c. In System/Preferences/Network Proxy type:

Direct Connection

With this, http_proxy variable will be blank and it will not confuse your Synaptic.


worked great for me.  thankyou so much been trying to figure this out for a few days now!!!

---

### Post by kOoLiNuS on 2006-11-29
Uhm, for me it worked  :p leaving these settings:

```
Acquire::http::Proxy "http://user:passwd@192.168.0.1:8080/";
```

in /etc/apt/apt.conf [1] AND specifing user:passwd@192.168.0.1 in the HTTP **and** FTP field in Synaptic.

On the System / Preferences / Network Proxy i deleted the setting and choose "direct connection" as suggested.


[1] else sudo apt-get update just hanged via terminal ...

---

### Post by Ockie87 on 2007-02-13
> **lauro.sa said:**
> **There are 2 ways:**

**1st. **Configure your synaptic (apt-get) proxy settings:

 a. Return your /etc/apt/apt.conf to the original:

*Acquire::http:Proxy "False";*

 b. In *Synaptic/Preferences/Network* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*
Proxy FTP:  *repeat*

 c. In *System/Preferences/Network Proxy* type:

*Direct Connection*

 With this, http_proxy variable will be blank and it will not confuse your Synaptic.

-------------------------------------------------------------

**2nd.** Configure your network proxy settings (http_proxy variable):

 a. Return your */etc/apt/apt.conf* to the original:

*Acquire::http:Proxy "False";*

 b. In *System/Preferences/Network Proxy* type:

Manual Proxy:
Proxy HTTP: *user:Passw@proxy*       PORT: *port*  DETAILS: *put user and passw again*
Proxy HTTPs:  *repeat*
Proxy FTP:  *repeat*
Host Socks:  *repeat*

 This works because the **http_proxy variable is mandatory **to Synaptic (apt-get).
 **[COLOR="Red"]The problem of this option is[/COLOR]**: with the command "echo $http_proxy" users can see your passw.

-------------------------------------------------------------

I tried your first method, but I got the following answer:
```
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
http://es.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

```


Also tried the second method and it didn't work neither.
Could this be a problem with closed ports?
Im at a student dorm, and I know most ports are closed...
For some reason synaptic gives the error when downloading file 23/34, which made me think that its using a port that isn't closed...

Thanks for the help in advance!

---

