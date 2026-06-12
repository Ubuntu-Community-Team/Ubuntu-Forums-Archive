---
title: "Package manager / repository problem"
date: 2010-01-07
forum: General Help
---

### Post by npattillo on 2010-01-07
I have an issue with my synaptic package manager. My PDF viewing capability disappeared and I think I screwed up a command line in terminal when I went to fix it (PDF viewing in firefox is still busted). Now I am getting this error;

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I know I have to somehow remove this in the repository and that there is some problem with unmet dependencies, I just need some help on getting that done. Please help! Thanks!!:D

---

### Post by oldos2er on 2010-01-07
Can you post the output of ```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by npattillo on 2010-01-07
I entered that with no problem. This is what I got back - HTML script...

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<noscript>
<meta http-equiv="refresh" content="0;url=http://webhelp.qwest.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=iil7m3f3h23ub7r46n5xmju72a5h65bb&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fmedibuntu.sos-sts.com%2Fsources.list.d%2Ffeisty.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0"/>
</noscript>
<script type="text/javascript">
window.location.replace("http://webhelp.qwest.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=iil7m3f3h23ub7r46n5xmju72a5h65bb&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fmedibuntu.sos-sts.com%2Fsources.list.d%2Ffeisty.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0");
</script>
</head>
<body>
</body>

---

### Post by lidex on 2010-01-07
Although I'm using that repository, I don't seem to have that entry. Checking other entries, the *.list files seem to contain one line of text which is the source location. Example: 
```
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main #Exaile
```
found in "exaile.list"

---

### Post by drs305 on 2010-01-07
That medibuntu.list file is corrupted. Run the following command. It will import the Medibuntu key and replace the medibuntu.list file with the correct one:
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by ajgreeny on 2010-01-07
Can you post the output of the terminal command ```
cat /etc/apt/sources.list.d/medibuntu.list
```That will show us what is wrong, but it should be very simple to correct by editing that file as root ```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

EDIT:  Too slow!  drs305 will get you to the same point in a slightly more direct manner.

---

### Post by npattillo on 2010-01-07
Thanks so much!! The command from drs305 fixed it! Thanks again for your help!!:P

---

