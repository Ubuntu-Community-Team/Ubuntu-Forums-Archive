---
title: "apt-get install chromium-browser = VirusFound"
date: 2012-02-08
forum: General Help
---

### Post by grahams on 2012-02-08
The update manager found a few updates as usual recently and failed to update chromium. When I looked into why I see the following output. 

The 403  VirusFound [IP: 91.189.92.167 80] is a little alarming

```
# sudo apt-get install -f chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-l10n chromium-codecs-ffmpeg
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 48 not upgraded.
Need to get 2,062kB/21.2MB of archives.
After this operation, 85.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1 [2,062kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1 [2,062kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1
  403  VirusFound [IP: 91.189.92.182 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1
  403  VirusFound [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_16.0.912.77~r118311-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_16.0.912.77~r118311-0ubuntu0.10.04.1_all.deb)  403  VirusFound [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by dcstar on 2012-02-09
> **grahams said:**
> The update manager found a few updates as usual recently and failed to update chromium. When I looked into why I see the following output. 

The 403  VirusFound [IP: 91.189.92.167 80] is a little alarming
.........
```
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1 [2,062kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1
  403  VirusFound [IP: 91.189.92.182 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.10.04.1
  403  VirusFound [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_16.0.912.77~r118311-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser-l10n_16.0.912.77~r118311-0ubuntu0.10.04.1_all.deb)  403  VirusFound [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

You are probably behind a Proxy server with AV that is falsely tagging these files and blocking them.

I have just manually download one of the files and scanned it with ClamAV and it was clean.

---

### Post by mcduck on 2012-02-09
> **dcstar said:**
> You are probably behind a Proxy server with AV that is falsely tagging these files and blocking them.

I have just manually download one of the files and scanned it with ClamAV and it was clean.

I'd agree with that answer, especially since the 403 error means "Forbidden", and there is no such substatus code as "VirusFound" for it. This seems like a proxy blocking the connection.

---

### Post by grahams on 2012-02-20
Thanks for the replies. 

This was triggering a virus alert in our work proxy server.

However I tried to install at home and although the files downloaded the install failed with "broken package". Looks like a bad package in the repo.

I've uninstalled chromium for chrome and that is working fine.

---

