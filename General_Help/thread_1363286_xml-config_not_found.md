---
title: "xml-config not found"
date: 2009-12-24
forum: General Help
---

### Post by shariefbe on 2009-12-24
Hello,
  I am using ubuntu and am trying to cofigure one file. But when i do ./configure i am getting that 

```

checking for ghttp_request_new in -lghttp... no
configure: warning: Cannot find libghttp: can't build gsthttpsrc
checking for xml-config... no
configure: error: Couldn't find xml-config
Configuration of glib library  has failed
root@ariem-desktop:/mnt/freescale/sources/gstreamer-0.0.4# 

```
Can anyone help me

---

### Post by s.fox on 2009-12-24
Hello,

Try some of the suggestions mentioned [here]("http://www.linuxquestions.org/questions/linux-software-2/xml-config-not-found-777868/").  Please post back if it doesn't resolve the problem :)

-Silver Fox

---

### Post by shariefbe on 2009-12-24
Actually i am compiling this for my arm board. Not for my host PC.
Npw i downloaded libxml2 and i compiled it for my arm processor. Now the things is i dot "xml2-config" file not a "xml-config" one.Now i am confused in configure file. How to change in that.

```

# Extract the first word of "xml-config", so it can be a program name with args.
set dummy xml-config; ac_word=$2
echo $ac_n "checking for $ac_word""... $ac_c" 1>&6
echo "configure:2576: checking for $ac_word" >&5
if eval "test \"`echo '$''{'ac_cv_path_XML_CONFIG'+set}'`\" = set"; then
  echo $ac_n "(cached) $ac_c" 1>&6
else
  case "$XML_CONFIG" in
  /*)
  ac_cv_path_XML_CONFIG="$XML_CONFIG" # Let the user override the test with a path.
  ;;
  ?:/*)
  ac_cv_path_XML_CONFIG="$XML_CONFIG" # Let the user override the test with a dos path.
  ;;
  *)
  IFS="${IFS=   }"; ac_save_ifs="$IFS"; IFS=":"
  ac_dummy="$PATH"
  for ac_dir in $ac_dummy; do
    test -z "$ac_dir" && ac_dir=.
    if test -f $ac_dir/$ac_word; then
      ac_cv_path_XML_CONFIG="$ac_dir/$ac_word"
      break
    fi
  done
  IFS="$ac_save_ifs"
  test -z "$ac_cv_path_XML_CONFIG" && ac_cv_path_XML_CONFIG="no"
  ;;
esac
fi
XML_CONFIG="$ac_cv_path_XML_CONFIG"
if test -n "$XML_CONFIG"; then
  echo "$ac_t""$XML_CONFIG" 1>&6
else
  echo "$ac_t""no" 1>&6
fi

if test x$XML_CONFIG = xno;then
  { echo "configure: error: Couldn't find xml-config" 1>&2; exit 1; }
fi
XML_LIBS=`xml-config --libs`
XML_CFLAGS=`xml-config --cflags`

```
In this which file should be changed as xml2-config and how to set the path for that file.
Thank you and kindly help me

---

