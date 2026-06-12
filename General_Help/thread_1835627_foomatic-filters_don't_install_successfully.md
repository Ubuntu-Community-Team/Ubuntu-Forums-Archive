---
title: "foomatic-filters don't install successfully"
date: 2011-08-29
forum: General Help
---

### Post by kswix on 2011-08-29
Hi guys, I try to install foomatic-filters, but see this:
```
root@misha:/home/misha/# sudo dpkg --force-depends --purge foomatic-filters
dpkg: foomatic-filters: &#1080;&#1084;&#1077;&#1102;&#1090;&#1089;&#1103; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099; &#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1103;&#1084;&#1080;, &#1085;&#1086; &#1087;&#1086; &#1074;&#1072;&#1096;&#1077;&#1084;&#1091; &#1091;&#1082;&#1072;&#1079;&#1072;&#1085;&#1080;&#1102;
&#1086;&#1085; &#1074;&#1089;&#1105; &#1088;&#1072;&#1074;&#1085;&#1086; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1076;&#1072;&#1083;&#1105;&#1085;:
 ubuntu-desktop &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090; &#1086;&#1090; foomatic-filters.
 foomatic-db-engine &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090; &#1086;&#1090; foomatic-filters (>= 4.0).
 foo2zjs &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090; &#1086;&#1090; foomatic-filters.
 pxljr &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090; &#1086;&#1090; foomatic-filters (>= 4.0.0~bzr156).
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; ... &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 181375 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1059;&#1076;&#1072;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; foomatic-filters ...
&#1042;&#1099;&#1095;&#1080;&#1097;&#1072;&#1102;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; foomatic-filters ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
Use of uninitialized value $template in length at /usr/share/perl5/Debconf/Question.pm line 212, <GEN0> line 1.
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; man-db ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN6> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN6> line 2.
root@misha:/home/misha/# 

```
So, I can remove this by sudo dpkg --force-depends --purge foomastic-filters, but this don't help successful reinstall it.

sudo dpkg --configure -a and sudo apt-get -f install don't work.

---

### Post by kswix on 2011-08-30
bump!

---

### Post by kswix on 2011-08-30
bump!

---

### Post by kswix on 2011-09-01
bump!

---

### Post by kswix on 2011-09-02
bump!

---

