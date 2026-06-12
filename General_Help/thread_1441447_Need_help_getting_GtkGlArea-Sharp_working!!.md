---
title: "Need help getting GtkGlArea-Sharp working!!"
date: 2010-03-28
forum: General Help
---

### Post by Goblin82 on 2010-03-28
Hi, I'm following the steps in [http://www.mono-project.com/GtkGlAreaSharp:Installation](http://www.mono-project.com/GtkGlAreaSharp:Installation) to get GtkGlArea-sharp working on my machine and then in Mono, everything installs (after a few days worth of problems to overcome) except when I go to configure gtkglarea-sharp.  I don't get an error but the config doesn't seem to detect my installation of Tao.  I checked in the opt/lib/mono/tao folder and all the appropriate files are there but the config returns this at the end:

```

Configuration summary for gtkglarea-sharp

   * Installation prefix: /home/goblin/opt
   * compiler: /usr/bin/gmcs
   * gtk-sharp-2.0: yes
   * Tao.OpenGl: no
   * Documentation: no (no)

```and when I scroll up I see this message:

```

checking for TAO_OPENGL_DEPENDENCIES... no
configure: WARNING: Tao.OpenGl not detected; examples will not be built

```everything else is fine but somehow it won't detect my installation of tao, any ideas?

---

