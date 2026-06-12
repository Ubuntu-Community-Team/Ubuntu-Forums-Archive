---
title: "Gimp problem and error"
date: 2011-03-08
forum: General Help
---

### Post by leon.alberti on 2011-03-08
Hi.
I use ubuntu for almost two years and this forum helped me a lot.
But now, my first time posting here, I don't find a solution anywhere for my problem.
Gimp won't start and when unistalled or installed it gives an error message (but install/unistall neverthless).

This is the message: 
installArchives() failed: (Lendo banco de dados ... 
[...]
Configurando gnome-backgrounds-hp (0.4) ...
update-alternatives: usando /usr/share/pixmaps/backgrounds/gnome/hp/default_background_solid.png para fornecer /usr/share/images/desktop-base/desktop-background (desktop-background) em modo automático.
update-alternatives: erro: impossível fazer com que /usr/share/images/desktop-base/desktop-background.dpkg-tmp fosse uma ligação simbólica para /etc/alternatives/desktop-background: Arquivo ou diretório não encontrado
dpkg: erro processando gnome-backgrounds-hp (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 2
No apport report written because MaxReports is reached already
Configurando gnome-backgrounds-hp (0.4) ...
update-alternatives: usando /usr/share/pixmaps/backgrounds/gnome/hp/default_background_solid.png para fornecer /usr/share/images/desktop-base/desktop-background (desktop-background) em modo automático.
update-alternatives: erro: impossível fazer com que /usr/share/images/desktop-base/desktop-background.dpkg-tmp fosse uma ligação simbólica para /etc/alternatives/desktop-background: Arquivo ou diretório não encontrado
dpkg: erro processando gnome-backgrounds-hp (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 2

Sorry for the portuguese, I hope it won't be hard to understand anyway.
I guess the error have something to do with the glassy blue theme of hp pcs I installed some time ago (and which I don't use)... I don't how to unistall this theme and I don't even know if this is the real problem.

Thanks in advance.

---

### Post by leon.alberti on 2011-03-08
Now I tired sudo apt-get remove --purge gnome-backgrounds-hp and still Gimp won't start...

---

### Post by leon.alberti on 2011-03-08
Disregard this thread.
I resolvedmy problem removing a conflicting ppa.

---

