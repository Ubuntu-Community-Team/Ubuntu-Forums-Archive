---
title: "Krdc error"
date: 2006-04-02
forum: General Help
---

### Post by jonnymccullagh on 2006-04-02
I have recently converted from Suse to kubuntu.
I am trying to connect to a Windows server using Krdc. I was able to do this with no issues on Suse but I get an error in kubuntu:
"Could not start kdesktop: make sure rdesktop is properly installed"

Do I need to configure something? Is this a known problem in kubuntu? Should I try re-installing?

any help is greatly appreciated,
thanks,
jonny

---

### Post by gingermark on 2006-04-02
I don't mean to ask a stupid question, but is rdesktop installed?

On my system Krdc is installed by default, but rdesktop isn't.

---

### Post by jonnymccullagh on 2006-04-02
Obviously there is no such thing as a stupid question because you were spot on.
Stupidly I thought that if krdc was there then that would be all I needed but I was wrong.
Thank you for your promt reply I just did a sudo apt-get install rdesktop
cheers,
jonny

---

### Post by gingermark on 2006-04-02
[QUOTE=jonnymccullagh]I thought that if krdc was there then that would be all I needed[/QUOTE]

I'm unfamiliar with Krdc, just suggested it cos of the error message you got. But I agree, it does seem odd rdesktop wasn't installed as well.

---

