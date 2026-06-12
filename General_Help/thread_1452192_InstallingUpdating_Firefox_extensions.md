---
title: "Installing/Updating Firefox extensions"
date: 2010-04-11
forum: General Help
---

### Post by ReeRD on 2010-04-11
Can Firefox extensions be safely installed "the right way", that is, via Firefox interface? Or is it preferred to use the package manager? Some extensions I'm interested in aren't available in the official repositories while those that are available are quite outdated.

---

### Post by mac9416 on 2010-04-11
Hi,

I have installed all my extensions through the Firefox interface and never had any trouble. As a matter of fact, I don't believe I've ever installed extensions through APT.

---

### Post by davidpbrown on 2010-04-11
The Firefox Addons are likely to keep themselves up to date faster than the repository copies. As you've seen, there seem to be few available in the repositories. I've never had problems removing them.

Last time I saw the idea of putting them in the repositories as standard was knocked back. It's only an issue on re-installation but re-adding them is simple enough, if you don't just upgrade. Also I don't know if there's an issue of forcing all users to have the same addon's if it's by repository rather than user choice otherwise..

---

### Post by lovinglinux on 2010-04-11
> **mac9416 said:**
> Hi,

I have installed all my extensions through the Firefox interface and never had any trouble. As a matter of fact, I don't believe I've ever installed extensions through APT.

+1

I currently have 51 extensions installed and a couple of others disable at the moment. I only install via Firefox. The only real benefit of installing extensions through Ubuntu repositories, is that you don't need to install them for each user. If you are the only user of your machine, than there is no benefit at all.

In terms of security, you are pretty much safe if download only extensions hosted by Mozilla. They have a very rigorous policy about accepting extensions and every new submission or update is reviewed by an editor. Additionally, hosted extensions are scanned for malware and when you submit the file, there is validation step, in which the site check for common security issues and other potential problems.

But keep in mind that not all extensions on Mozilla site are hosted by them. There are basically three types of extensions: approved, experimental and self-hosted:

1 - Hosted on Mozilla, reviewed by an editor and scanned for malware
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152986&stc=1&d=1271027647[/IMG]

2 - Hosted on Mozilla, scanned for malware but NOT reviewed or NOT approved yet
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152987&stc=1&d=1271027647[/IMG]

3 - NOT hosted on Mozilla, NOT scanned for malware, NOT reviewed (ever)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152988&stc=1&d=1271027647[/IMG]

The ones in the second and third category should be avoided, unless you trust the developer. 

Any extension, has the potential to cause problems, not matter if they are from Ubuntu repositories, from Mozilla web site or somewhere else. Some problems only appear when two extensions interact with each other. Nevertheless, I never saw any approved extension causing damage to the system, only causing odd behavior on Firefox.

Also read the Privacy Police of each extension, since some types of extensions need to collect data from your system.

---

### Post by ReeRD on 2010-04-12
All right, thanks, will do it the usual Firefox way.

---

