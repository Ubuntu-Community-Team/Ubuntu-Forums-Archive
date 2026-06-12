---
title: "Security Devices in Evolutoin"
date: 2011-06-25
forum: General Help
---

### Post by ocwo92 on 2011-06-25
I need to install a security device for signing my email messages with a personal certificate. Thunderbird allows me to install a "Security Device" in the form of a ".so" library that handles the authentication. Is it possible to install security devices in Evolution, too, and if so, how do I do that?

---

### Post by ocwo92 on 2011-06-25
I attempted the work-around described _[here]("http://www.mail-archive.com/evolution@lists.ximian.com/msg10447.html")_, substituting ~/.mozilla/<user>/<random>/ with ~/.thunderbird/<random> and ~/.evolution with ~/.local/share/evolution, but this doesn't seem to work for me.

---

### Post by Zill on 2011-06-25
ocwo92:  This link may help explain things...

[http://library.gnome.org/users/evolution/stable/encryption.html.en]("http://library.gnome.org/users/evolution/stable/encryption.html.en")

---

### Post by ocwo92 on 2011-06-25
> **Zill said:**
> ocwo92:  This link may help explain things...

Well, yes and no. I already have a PGP key that I can use for signing, and I also have a _[CAcert]("http://www.cacert.org")_ certificate that I can use for S/MIME signing.

However, the certificate that is giving me headaches is one that is provided by a national, centralized agency, which unfortunately doesn't comply well with neither standards nor common sense. (For example, this national agency insists on owning our private keys, which are stored centrally; but that's all a different story.) To sign the certificate, the agency provides a "security device" that works in Thunderbird, and I'm wondering if this can somehow be put to use by Evolution, too.

---

### Post by Zill on 2011-06-25
ocwo92:  I have not used a "security device" as you have described but would have thought that it still involves a certificate file that can be imported into Evolution as described under para "[2.6.6.1.&#8195;Adding a Signing Certificate]("http://library.gnome.org/users/evolution/stable/encryption.html.en#bspyee8")".

However, anyone who has actually used such a device will probably be able to give better advice than me. ;-)

It may help clarification if you can advise if the "security device" is hardware (such as a dongle) or software and how it is currently used.

---

### Post by ocwo92 on 2011-06-25
> **Zill said:**
> ocwo92:  I have not used a "security device" as you have described but would have thought that it still involves a certificate file that can be imported into Evolution as described under para "[2.6.6.1.&#8195;Adding a Signing Certificate]("http://library.gnome.org/users/evolution/stable/encryption.html.en#bspyee8")".
It would probably work if the certificate authority wasn't violating several security issues. In this case, however, I can't simply import the certificate.

The "security device" is a piece of software, that is, a library that works with Thunderbird. This piece of software handles a certificate that seems to be a PCKS11 format that is embedded in some proprietary format.

---

