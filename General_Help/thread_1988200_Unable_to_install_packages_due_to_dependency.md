---
title: "Unable to install packages due to dependency"
date: 2012-05-27
forum: General Help
---

### Post by rraj.be on 2012-05-27
When ever im trying to install something im getting the following dependency error


```

Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-23-generic-pae : Depends: linux-headers-3.2.0-23 but it is not going to be installed
 linux-image : Depends: linux-image-generic (= 3.0.0.19.23) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

This is my linux instalation info

```

raj@raj-VPCEB46FG:~$ uname -a
Linux raj-VPCEB46FG 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux
raj@raj-VPCEB46FG:~$ 

```

I dont have synaptic installed.
i generally use sudo apt-get or software center rarely
Tried to repair with ubuntu software-centerand below is the error with that.


```


installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.19.23); however:
  Package linux-image-generic is not installed.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image
Error in function: 
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.19.23); however:
  Package linux-image-generic is not installed.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
```


Any help to resolve this please?

> sudo apt-get update works fine..

---

### Post by oldos2er on 2012-05-27
Have you tried running ```
sudo apt-get -f install
```

---

### Post by ingramproductions on 2012-05-27
Dude!

---

### Post by Old_Grey_Wolf on 2012-05-27
> **ingramproductions said:**
> Dude!

It took my a while to figure out what that meant. :) I didn't notice the typo in the thread title.

---

