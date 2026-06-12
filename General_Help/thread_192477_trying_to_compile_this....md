---
title: "trying to compile this..."
date: 2006-06-08
forum: General Help
---

### Post by Therrol on 2006-06-08
okay, I'm having no luck compiling this GIMP plugin. Maybe I need to install something? Help is appreciated.

here is the plugin: [http://leuksman.com/pages/icns](http://leuksman.com/pages/icns)

and here is my error, it's way too long to post, and I can't scroll to the top it's so long.
 this is the end of it.
/usr/include/gimp-2.0/libgimp/gimpprogressbar.h:61: error: syntax error before ‘gimp_progress_bar_get_type’
/usr/include/gimp-2.0/libgimp/gimpprogressbar.h:61: error: syntax error before ‘G_GNUC_CONST’
/usr/include/gimp-2.0/libgimp/gimpprogressbar.h:61: warning: data definition has no type or storage class
/usr/include/gimp-2.0/libgimp/gimpprogressbar.h:63: error: syntax error before ‘*’ token
/usr/include/gimp-2.0/libgimp/gimpprogressbar.h:63: warning: data definition has no type or storage class
In file included from /usr/include/gimp-2.0/libgimp/gimpui.h:40,
                 from main.c:30:
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:27: error: syntax error before ‘G_BEGIN_DECLS’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:32: error: syntax error before ‘typedef’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:32: error: syntax error before ‘image_id’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:34: error: ‘GimpDrawableConstraintFunc’ declared as function returning a function
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:37: error: syntax error before ‘*’ token
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:38: error: syntax error before ‘gpointer’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:38: warning: data definition has no type or storage class
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:39: error: syntax error before ‘*’ token
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:40: error: syntax error before ‘gpointer’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:40: warning: data definition has no type or storage class
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:41: error: syntax error before ‘*’ token
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:42: error: syntax error before ‘gpointer’
/usr/include/gimp-2.0/libgimp/gimpdrawablecombobox.h:42: warning: data definition has no type or storage class
In file included from /usr/include/gimp-2.0/libgimp/gimpui.h:41,
                 from main.c:30:
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:27: error: syntax error before ‘G_BEGIN_DECLS’
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:32: error: syntax error before ‘typedef’
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:32: error: syntax error before ‘image_id’
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:33: error: ‘GimpImageConstraintFunc’ declared as function returning a function
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:36: error: syntax error before ‘*’ token
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:37: error: syntax error before ‘gpointer’
/usr/include/gimp-2.0/libgimp/gimpimagecombobox.h:37: warning: data definition has no type or storage class
In file included from main.c:30:
/usr/include/gimp-2.0/libgimp/gimpui.h:44: error: syntax error before ‘G_BEGIN_DECLS’
/usr/include/gimp-2.0/libgimp/gimpui.h:49: error: syntax error before ‘void’
/usr/include/gimp-2.0/libgimp/gimpui.h:49: error: syntax error before ‘*’ token
In file included from main.c:34:
main.h:25: error: syntax error before ‘extern’
main.h:40: error: syntax error before ‘gint32’
main.h:40: warning: no semicolon at end of struct or union
main.h:41: warning: data definition has no type or storage class
main.h:42: warning: data definition has no type or storage class
main.h:46: error: syntax error before ‘gint32’
main.h:46: warning: no semicolon at end of struct or union
main.h:47: warning: data definition has no type or storage class
main.h:48: error: syntax error before ‘cursor’
main.h:48: error: conflicting types for ‘cursor’
/usr/include/gimp-2.0/libgimpwidgets/gimppickbutton.h:43: error: previous declaration of ‘cursor’ was here
main.h:48: warning: data definition has no type or storage class
main.h:49: error: syntax error before ‘*’ token
main.h:49: error: conflicting types for ‘data’
/usr/include/gimp-2.0/libgimpbase/gimpparasite.h:48: error: previous declaration of ‘data’ was here
main.h:49: warning: data definition has no type or storage class
main.h:50: error: syntax error before ‘}’ token
main.h:50: warning: data definition has no type or storage class
main.h:54: error: syntax error before ‘fourcc’
main.h:55: error: syntax error before ‘*’ token
In file included from main.c:35:
icnsdata.h:6: error: syntax error before ‘gint32’
icnsdata.h:6: warning: no semicolon at end of struct or union
icnsdata.h:7: warning: data definition has no type or storage class
icnsdata.h:8: error: syntax error before ‘height’
icnsdata.h:8: warning: data definition has no type or storage class
icnsdata.h:9: error: syntax error before ‘bits’
icnsdata.h:9: warning: data definition has no type or storage class
icnsdata.h:10: error: syntax error before ‘mask’
icnsdata.h:10: warning: data definition has no type or storage class
icnsdata.h:11: warning: data definition has no type or storage class
icnsdata.h:13: error: syntax error before ‘iconTypes’
icnsdata.h:13: warning: data definition has no type or storage class
icnsdata.h:14: error: syntax error before ‘maskTypes’
icnsdata.h:14: warning: data definition has no type or storage class
icnsdata.h:15: error: syntax error before ‘icns_colormap_4’
icnsdata.h:15: warning: data definition has no type or storage class
icnsdata.h:16: error: syntax error before ‘icns_colormap_8’
icnsdata.h:16: warning: data definition has no type or storage class
In file included from main.c:36:
icnsload.h:25: error: syntax error before ‘LoadICNS’
icnsload.h:25: error: syntax error before ‘*’ token
icnsload.h:25: warning: data definition has no type or storage class
main.c:43: error: function ‘interactive_ico’ is initialized like a variable
main.c:43: error: ‘FALSE’ undeclared here (not in a function)
main.c:46: error: syntax error before ‘*’ token
main.c: In function ‘query’:
main.c:66: error: array type has incomplete element type
main.c:72: error: array type has incomplete element type
main.c:77: error: array type has incomplete element type
main.c:77: error: storage size of ‘save_args’ isn’t known
main.c:72: error: storage size of ‘load_return_vals’ isn’t known
main.c:66: error: storage size of ‘load_args’ isn’t known
main.c: At top level:
main.c:122: error: syntax error before ‘*’ token
main.c: In function ‘run’:
main.c:129: error: ‘gint32’ undeclared (first use in this function)
main.c:129: error: (Each undeclared identifier is reported only once
main.c:129: error: for each function it appears in.)
main.c:129: error: syntax error before ‘image_ID’
main.c:135: error: ‘param’ undeclared (first use in this function)
main.c:137: error: ‘nreturn_vals’ undeclared (first use in this function)
main.c:138: error: ‘return_vals’ undeclared (first use in this function)
main.c:142: warning: passing argument 1 of ‘strcmp’ from incompatible pointer type
main.c:147: error: ‘TRUE’ undeclared (first use in this function)
main.c:152: error: ‘nparams’ undeclared (first use in this function)
main.c:162: error: ‘image_ID’ undeclared (first use in this function)
main.c: At top level:
main.c:226: error: syntax error before ‘fourcc’
main.c: In function ‘fourcc_get_string’:
main.c:228: error: ‘gint32’ undeclared (first use in this function)
main.c:228: error: syntax error before ‘)’ token
main.c:228: error: ‘fourcc’ undeclared (first use in this function)
main.c: At top level:
main.c:232: error: syntax error before ‘*’ token
main.c: In function ‘hexdump’:
main.c:234: error: ‘guint’ undeclared (first use in this function)
main.c:234: error: syntax error before ‘i’
main.c:235: error: ‘i’ undeclared (first use in this function)
main.c:235: error: ‘nbytes’ undeclared (first use in this function)
make: *** [main.o] Error 1

---

### Post by hanzomon4 on 2006-06-08
Try this ```
sudo apt-get install build-essential
```
Then try compiling again
Good luck :wink:

---

### Post by Therrol on 2006-06-10
hmm, my build essentials package is latest version.

is there some GIMP developer packages I should install?

---

