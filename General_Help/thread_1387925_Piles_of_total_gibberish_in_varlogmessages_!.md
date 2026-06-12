---
title: "Piles of total gibberish in /var/log/messages !?"
date: 2010-01-22
forum: General Help
---

### Post by robgwin on 2010-01-22
I've got Ubuntu 9.10 on a Dell Vostro 420 desktop. Every now and then it freezes and crashes at random times (either while I'm working on something timid like a plaintext email, or while it's just sitting there), and requires a hard reboot. Seems like a RAM problem to me, but the memory tests always come out 100% successful, grr.

But anyway, here's why I'm posting. After one such crash today, I took a peek at /var/log/messages. First I noticed the latest version of this file (covering only the last 3 days) had grown to 51M. And it's almost entirely composed of completely random-*** gibberish. W.. T.. F? Has anybody ever seen something like this? Any clue what the deal is? I have not installed anything weird on this machine, I don't even use compiz. I just use vanilla standard apps, like evolution, firefox, etc.

```
Jan 21 18:08:50 monkey kernel: [35365.730730] r8169: eth0: link up
Jan 22 05:58:01 monkey kernel: [77917.417593] ------------[ cut here ]------------
Jan 22 05:58:01 monkey kernel: [77917.417597] ------------[ cut here ]------------
Jan 22 05:58:01 monkey kernel: [77917.417606] WARNING: at /build/bucbp s<ni_7i1s70<r7d06Rik1d11xr47o[7p]91ee89e<7uid7l0xe]3a597aid2tr]77<-u>4dk5cs[h[74ddi<x]>7n0m 79a7967kafr77r4__]m7p sx6
Jan 22 05:58:01 monkey kernel: 7_io
Jan 22 05:58:01 monkey kernel: 9__wh7s 1<: dddcoh xr_0tsc> li3<m57 89[<2c110+/4cu017fet
Jan 22 05:58:01 monkey kernel: l5dr77x3de33ecf 81a64[<xdp[tiea91<r9xg9
Jan 22 05:58:01 monkey kernel: ]uie7672mea+c5 bw2_7_ 7[ 8c40eet9870 n44Ve11
Jan 22 05:58:01 monkey kernel: k6>prf> /r7tuo [d/07[1-11t
Jan 22 05:58:01 monkey kernel: 84a001m1 c 1>p777rer084 g 8[_<[e9le1 7r70[7e7s-n4onn]m01q n+3ea1rc 7et a7+ikc23.5>d72
Jan 22 05:58:01 monkey kernel: ca4- 0]94_ c?e0>158.i7eh _>m<71eu_]i/1s>m-[i.]ee1-6eelid/d_
Jan 22 05:58:01 monkey kernel: ts5a45.ica4  195n-f7b+n020 ]5944 8]<pSk4700/+ [7<rbb>744ru/47 +7 e1l]-8>5ms20[1t9uo]3m <.0fvgkeo5<8>td327u pW7e0c>l7rb-0a77i446/se7m0d4cybcf<idaide01_87to0i89<7aw680c9721se04[[1u77400b1e 7e.t77ac /r<>_<<kfpa920i74 ]14d <r>475cidr-+u851e1scn8-ban4_7ks
Jan 22 05:58:01 monkey kernel: aqt_w929di5ews3 .120t
Jan 22 05:58:01 monkey kernel: xU6]
Jan 22 05:58:01 monkey kernel: .m4_]i9<r7<>7 . [1t3[ c.00l3]e4i[n0514Nftcrn2cde+4
Jan 22 05:58:01 monkey kernel: d_snq_ienr7 g i08cs4.09 i>_ 4.ut4>7pc7k00. ]07+>a_8]4d>dxxbcp66p gslhl7_73
Jan 22 05:58:01 monkey kernel: 5a0i_3_fd4i  _r><m6[r].7[r>trp56i<]i[8pce3+4nn80ix[e[4
Jan 22 05:58:01 monkey kernel: l c[9-[.7:645no6<24_[NHsidoyleipse181
Jan 22 05:58:01 monkey kernel: +/1 81n8031tx751 dseg04c[2_
Jan 22 05:58:01 monkey kernel: t0xxsn4x18>r34918s]013b5/> n-tn0m1afo+sls-b74dbis  deu_er4e1hc711+1o r iin 1492s<0b18
Jan 22 05:58:01 monkey kernel: s<70d2e712aa-4 40n5da4_0pt.r[  +rs_i4 <d3
Jan 22 05:58:01 monkey kernel: >a9c1  a_.2<e1 d01pe<tbdm4u 9tks9e1c7?k
Jan 22 05:58:01 monkey kernel: tam]V5<cf2
Jan 22 05:58:01 monkey kernel: l .adnbdo scpa2[9 ]+00>d_hi94-sScde41xyou]4i]5>b/a
Jan 22 05:58:01 monkey kernel: p. .93ee.]]2sn as><e i96477ii 74m i0]/t2+xmgcad9xn[<i /4e
Jan 22 05:58:01 monkey kernel: [_g9i11us2a7ceo _.o9s]i .t7d0r_c5/
Jan 22 05:58:01 monkey kernel: 0ncat_797m5k ee] x
Jan 22 05:58:01 monkey kernel: 0euire_ [ii0
Jan 22 05:58:01 monkey kernel: rn_8/1c-7b7me<x004ecm>0sn94x t[3.0ro< x>]<_u4i---4w?4c9rt ihs s_sai8a0049b09? 17 7410.7nx po_6.96d0e]x_90cv03[<cb>3Sb [>617a0lnb177a  y1 _0qi[5 ii_][ 72x>1<_221 --u.Hrxisit90l07_
Jan 22 05:58:01 monkey kernel: 4d  xwamx1ld/0at1:afi

```

... and on and on and on like this ...

---

### Post by BobVila on 2010-01-22
What's in your /build directory?

---

### Post by woodmaster on 2010-01-23
I get pretty much the same gibberish...will check on the /build directory when I get home to my Buntu machine

---

