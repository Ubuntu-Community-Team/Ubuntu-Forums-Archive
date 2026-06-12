---
title: "Urgen help needed to reply a prompt while compiling gnome shell..."
date: 2009-12-02
forum: General Help
---

### Post by emigrant on 2009-12-02
hi all,
what should i give for this:
```

...
cc1: warnings being treated as errors
compositor/mutter-texture-tower.c: In function ‘mutter_texture_tower_set_base_texture’:
compositor/mutter-texture-tower.c:171: error: ‘cogl_offscreen_unref’ is deprecated (declared at /home/arshad/gnome-shell/install/include/clutter-1.0/cogl/cogl-offscreen.h:98)
compositor/mutter-texture-tower.c: In function ‘texture_tower_revalidate_fbo’:
compositor/mutter-texture-tower.c:462: error: ‘cogl_push_draw_buffer’ is deprecated (declared at /home/arshad/gnome-shell/install/include/clutter-1.0/cogl/cogl.h:833)
compositor/mutter-texture-tower.c:463: error: ‘cogl_set_draw_buffer’ is deprecated (declared at /home/arshad/gnome-shell/install/include/clutter-1.0/cogl/cogl.h:823)
compositor/mutter-texture-tower.c:478: error: ‘cogl_pop_draw_buffer’ is deprecated (declared at /home/arshad/gnome-shell/install/include/clutter-1.0/cogl/cogl.h:842)
make[4]: *** [mutter-texture-tower.o] Error 1
make[4]: Leaving directory `/home/arshad/gnome-shell/source/mutter/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/arshad/gnome-shell/source/mutter/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/arshad/gnome-shell/source/mutter/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arshad/gnome-shell/source/mutter'
make: *** [all] Error 2
*** error during stage build of mutter: ########## Error running make   *** [5/7]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice: 

```

thank you very much.:popcorn:

---

### Post by MacUntu on 2009-12-02
I'd delete everything and start over: [http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98](http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98) (watch the output for missing dependencies).

I build the shell just two hours ago so I'm positive it should work.

---

### Post by emigrant on 2009-12-02
buddy thanks for your input,
i too solved it by removing the jhbuild for jaunty and installing the debian jhbuild. :)

thanks again. :)

---

