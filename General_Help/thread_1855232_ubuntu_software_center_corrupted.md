---
title: "ubuntu software center corrupted"
date: 2011-10-05
forum: General Help
---

### Post by juanEcuador on 2011-10-05
Hi
i downloaded google chrome.deb file, the double clicked it and ubuntu software center started.. or at least it seemed like so. yet the whole window is empty like blacked out, i closed then reopened it but it was still the same. Please help me for i dont know how to fix it, and im pretty much a noob on ubuntu.

whatever help you may have i gladly accept it, thanks  :(

---

### Post by matt_symes on 2011-10-05
Hi

Open a terminal and type

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen.

Post the results back here by copy and pasting the text in the terminal. Post the results between code tags like this

[noparse] ```
 results 
```[/noparse]

It will show up in your next post like this

```
 results 
```Kind regards

---

### Post by juanEcuador on 2011-10-06
thank you very much for the quick response, before reading it i  restarted the pc which seemed to fix the problem, even though did what  you suggested and these were the results

```
 
W: GPG error: http://packages.medibuntu.org natty 

InRelease: The  following signatures couldn't be verified because the public key is not  available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch http://apt.boxee.tv/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. 

```so my questions are
how do i make the public key available?
why would  it fail to fetch boxee-related if i already removed boxee package?
how do i fix the index files failure and GPG error? - i dont quite understand what are these

got to say this got me started on the documentation, im pretty sure had i known a little more about the system i would have been able to fix it properly before 

and again thank you for your time and help, :smile:

---

### Post by amjjawad on 2011-10-06
Hello and Welcome :)

Have you installed any PPA to your system?

---

### Post by mcduck on 2011-10-06
Like the errors tell you, you have added both Medibuntu repository, and a repository for Boxee. 

When you added the Medibuntu repository, you forgot to add the signing key for it. To fix that you can simply follow the second step of the instructions from the Medibuntu web site: 
```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

...and it seems that the Boxee repository doesn't even exist any more, or has moved to some other location. You should simply remove it from your software sources.

---

### Post by juanEcuador on 2011-10-06
Hi amjjawad - yes i`ve installed PPA to the system, mainly through *.deb files, some other through terminal thanks to comand on the web, is that something wrong? :(

---------------------------------------------------

mcduck - thanks for the medibuntu failure correction, worked perfectly, but as you said the boxee package is already removed, thats why i find that ackward :confused:

---

### Post by juanEcuador on 2011-10-06
As an update to the my boxee error, i went to software source - other software and unchecked the boxee-related item and voilà its fixed

again that you all for your time and help..

got to say im loving ubuntu; and this community has proven to be fast and friendly on helping others

keep it up and hope someday ill be able to help too  :guitar:

---

### Post by amjjawad on 2011-10-06
> **juanEcuador said:**
> keep it up and hope someday ill be able to help too  :guitar:

You already did by marking this thread as SOLVED ;)
If someone else having the same issue, he/she will find your thread and probably follow the same steps and fix the problem :)

ALL THE BEST and welcome to the family :)

---

