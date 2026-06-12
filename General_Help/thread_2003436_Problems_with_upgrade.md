---
title: "Problems with upgrade"
date: 2012-06-14
forum: General Help
---

### Post by miguelpires on 2012-06-14
Hello,
When i run the update of my 12.04 64 bits system i received this message:


W: Ocorreu um erro durante a verificação da assinatura. O repositório não está actualizado e serão utilizados os ficheiros anteriores de índice. Erro do GPG: [http://dl.google.com](http://dl.google.com) stable Release: As seguintes assinaturas eram inválidas: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: Falhou obter [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  

W: Alguns arquivos index falharam ao ser baixados. Eles foram ignorados, ou cópias antigas são usadas ao invés.

Anyone have the same problem?

Regard's
Miguel Pires

---

### Post by dcstar on 2012-06-14
> **miguelpires said:**
> Hello,
When i run the update of my 12.04 64 bits system i received this message:


W: Ocorreu um erro durante a verificação da assinatura. O repositório não está actualizado e serão utilizados os ficheiros anteriores de índice. Erro do GPG: [http://dl.google.com](http://dl.google.com) stable Release: As seguintes assinaturas eram inválidas: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: Falhou obter [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  

W: Alguns arquivos index falharam ao ser baixados. Eles foram ignorados, ou cópias antigas são usadas ao invés.

Anyone have the same problem?

Regard's
Miguel Pires

Google is not an official repository, remove it from your system and add it back in later (if necessary).

---

### Post by miguelpires on 2012-06-14
> **dcstar said:**
> Google is not an official repository, remove it from your system and add it back in later (if necessary).

Strange?! This was add when I install chrome.

---

### Post by markbl on 2012-06-14
It's a bug currently exhibited by Google.

Workaround is to change "chrome" to "chrome_testing" in the deb line in /etc/apt/sources.list.d/google-chrome.list file and do another update.

---

### Post by markbl on 2012-06-14
Google/chromium have now fixed the bug, so the workaround I mention above is no longer required. Fix mentioned at [http://code.google.com/p/chromium/issues/detail?id=132711](http://code.google.com/p/chromium/issues/detail?id=132711).

---

