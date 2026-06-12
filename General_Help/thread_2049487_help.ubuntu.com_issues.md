---
title: "help.ubuntu.com issues"
date: 2012-08-28
forum: General Help
---

### Post by Urhixidur on 2012-08-28
The help.ubuntu.com pages are editable, wiki-style, but lack talk pages, which means problems with the contents have to be brought elsewhere.  No clear indications exist, so I ended up here.  No forum dedicated to this category that I could find.

Onward to specifics:

On the "Repositories/Ubuntu" page (help.ubuntu.com/community/Repositories/Ubuntu), the "Authentication Tab" section is opaque to the point of unhelpfulness.  It reads simply:[INDENT]"Authentication keys" are usually obtained from the  maintainer of the software repository. The maintainer will often place a  copy of the authentication key on a public key server such as  [www.keyserver.net]("http://www.keyserver.net"). The key can then be retrieved using the command:
[/INDENT]
[LIST]
[*]gpg --keyserver [name of keyserver] --recv-keys [keyhash]
[/LIST]

[LIST]
[*]In our example above, you would import the maintainer's authentication key as follows:
[/LIST]

[LIST]
[*]gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
[/LIST]

[LIST]
[*]Then, add the key to Ubuntu's apt trusted keys database with the following command
[/LIST]

[LIST]
[*]gpg --export --armor 1135D466 | sudo apt-key add -
[/LIST]
First, the "example above" appears non-existent.  A jump to an anchor would be needed once the apparently missing example is re-inserted into the text.  Second, and foremost, the authentication key hash 1135D466 was obtained how?  It is not mentioned anywhere else on the page, and does not appear in any image either.  I came to this page precisely to find out how to obtain a repository's key (when it isn't clearly supplied a s a root file).  gpg clearly requires a key hash, but how is said key hash obtained?  This is not explained at all.

---

### Post by Zill on 2012-08-28
> **Urhixidur said:**
> ... I came to this page precisely to find out how to obtain a repository's key (when it isn't clearly supplied a s a root file).  gpg clearly requires a key hash, but how is said key hash obtained?  This is not explained at all.
The keys for the default repositories should be included automatically.  You only need to add these manually if you add further repos yourself.

If you *do* choose to add a repo then, as the Wiki article states, the signing key should be obtained from the maintainer of the software repository.  For example, if you want to add the [PPA for Mozilla Team]("https://launchpad.net/~mozillateam/+archive/ppa") then the key (1024R/CE49EC21) is shown when you click on the link entitled "Technical details about this PPA".  The latter part of this is the key shown in the Wiki article screenshot.

I hope this clarifies things.

---

### Post by Urhixidur on 2012-08-29
> **Zill said:**
> If you *do* choose to add a repo then, as the Wiki article states, the signing key should be obtained from the maintainer of the software repository.  For example, if you want to add the [PPA for Mozilla Team]("https://launchpad.net/%7Emozillateam/+archive/ppa") then the key (1024R/CE49EC21) is shown when you click on the link entitled "Technical details about this PPA".  The latter part of this is the key shown in the Wiki article screenshot.

I hope this clarifies things.

It doesn't address the page's other glaring deficiencies (non-existent quoted example, etc.), but it is nevertheless progress.  Is there any way of obtaining the key hash from, for instance, signatures?  For instance, suppose I wanted to find out the key hash of extras.ubuntu.com (3e5c1192 according to Synaptic).  Synaptic must obtain it from somewhere on that web site, but browsing it yields no obvious answer.  If obtaining a key hash is deliberately obscure, this should be stated.

The anterior reason I stumbled into this quagmire was to try to resolve an "unauthenticated sources" error message from the Update manager (linux-headers-* packages).  It is currently so bad I can't even install Synaptic itself!

---

### Post by Zill on 2012-08-29
> **Urhixidur said:**
> ...The anterior reason I stumbled into this quagmire was to try to resolve an "unauthenticated sources" error message from the Update manager (linux-headers-* packages).  It is currently so bad I can't even install Synaptic itself!
Please run the following command and then post the corresponding output, using "CODE" tags for clarity.
```
sudo apt-get update
```

---

### Post by Urhixidur on 2012-08-29
> **Zill said:**
> Please run the following command and then post the corresponding output, using "CODE" tags for clarity.
```
sudo apt-get update
```

Following the error message issued by apt-get install (fromthe command line), I did try that and it did fix the problem.  I've simultaneously filed a bug against synaptic for its failure to a) offer to install unauthorised packages like the command line does, and b) failing to update properly on its own (or maybe that is a distinct Update Manager bug?).

---

### Post by Zill on 2012-08-29
Urhixidur:  I am pleased that you have now fixed the problem.

Please now mark this thread as "Solved" via the "Thread Tools" menu near the top right-hand corner of this forum thread screen.  Only the original poster can do this.

---

### Post by Urhixidur on 2012-09-05
> **Zill said:**
> Urhixidur:  I am pleased that you have now fixed the problem.

Please now mark this thread as "Solved" via the "Thread Tools" menu near the top right-hand corner of this forum thread screen.  Only the original poster can do this.

I've rewritten the offending section of [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to reflect what I've learned here. Please take a look and see if I got it right.

---

