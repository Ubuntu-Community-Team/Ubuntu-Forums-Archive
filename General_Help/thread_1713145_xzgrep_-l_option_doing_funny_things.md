---
title: "xzgrep -l option doing funny things"
date: 2011-03-23
forum: General Help
---

### Post by hwttdz on 2011-03-23
I have a relatively large database of files which I keep xz-zipped to save space, and I'm interested in finding all files which contain a certain term.  I am attempting to use xzgrep -l, but I get a "grep: -q: No such file or directory" when I run this, running xzgrep term file.xz, gives the expected result.  Any thoughts?

---

### Post by gmargo on 2011-03-23
It's a bug in the **/usr/bin/xzgrep** shell script.

This patch will fix it.  See the two places where "-q" is added to the grep command:
```

--- xzgrep.00   2010-05-31 03:35:56.000000000 -0700
+++ xzgrep      2011-03-23 15:43:02.282772480 -0700
@@ -156,9 +156,9 @@
     exec 5>&1
     ($uncompress -- "$i" 5>&-; echo $? >&5) 3>&- |
     if test $files_with_matches -eq 1; then
-      eval "$grep" -q && { printf '%s\n' "$i" || exit 2; }
+      eval "$grep" >/dev/null && { printf '%s\n' "$i" || exit 2; }
     elif test $files_without_matches -eq 1; then
-      eval "$grep" -q || {
+      eval "$grep" >/dev/null || {
         r=$?
         if test $r -eq 1; then
           printf '%s\n' "$i" || r=2

```

---

### Post by hwttdz on 2011-03-23
Thanks that sorted it.  What's the source of the patch?  Is that going to be pushed to the repo?

---

### Post by gmargo on 2011-03-23
I saw that the -q was the problem, and then compared the xzgrep script to /bin/zgrep, which used the >/dev/null syntax.

I've communicated with the author via IRC, so he is now aware.

---

### Post by gmargo on 2011-03-23
Ultimately we came up with a slightly different patch, in order to keep the -q option for speed.  The fix is now in the repo.  Thanks go to Larhzu at [http://tukaani.org/xz/](http://tukaani.org/xz/)

```

$ diff -u xzgrep.00 xzgrep
--- xzgrep.00   2010-05-31 03:35:56.000000000 -0700
+++ xzgrep      2011-03-23 16:50:04.433687303 -0700
@@ -126,6 +126,10 @@
   grep="$grep $option$optarg"
 done
 
+if test $files_with_matches -eq 1 || test $files_without_matches -eq 1; then
+  grep="$grep -q"
+fi
+
 eval "set -- $operands "'${1+"$@"}'
 
 if test $have_pat -eq 0; then
@@ -156,9 +160,9 @@
     exec 5>&1
     ($uncompress -- "$i" 5>&-; echo $? >&5) 3>&- |
     if test $files_with_matches -eq 1; then
-      eval "$grep" -q && { printf '%s\n' "$i" || exit 2; }
+      eval "$grep" && { printf '%s\n' "$i" || exit 2; }
     elif test $files_without_matches -eq 1; then
-      eval "$grep" -q || {
+      eval "$grep" || {
         r=$?
         if test $r -eq 1; then
           printf '%s\n' "$i" || r=2

```

---

