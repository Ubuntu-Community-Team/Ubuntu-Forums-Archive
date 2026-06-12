---
title: "Matlab/Comsol problems"
date: 2009-08-04
forum: General Help
---

### Post by IstariAsuka on 2009-08-04
Hi all, I'm relatively a linux noob still, so please keep that in mind.  I'm running 9.04 (32 bit), and have been setting up some software, namely matlab and comsol. Both installed great. Then the problems start.  

First, I can start matlab from the console. Seems to start up and work great. However, if I try to start it via the gui it starts the splashscreen but then dies. Moreover, the "matlab" and "matlab_helper" processes are still there, and have to be killed manually.  

Moving on to comsol, I can open it via gui or console fine, and it seems to work fine. However, comsol and matlab integrate with each other, which I can initiate by opening comsol via "comsol matlab" command, which starts up the matlab environment, from which I can type "comsol" to start up comsol such that it's connected to matlab. When I run "comsol matlab", it throws an error in the console (cat: ~/MATLAB/sys/java/jre/glnx86/jre.cfg: No such file or directory), though matlab still starts up despite this, and matlab says it has successfully established a new client connection when I invoke comsol from the matlab command line.  

Now, the real problem comes when I then perform an action in comsol which involves matlab. Matlab dies. Comsol tries to reconnect to matlab, in vain (sometimes crashing, and forcing me to kill java to get rid of the remnant windows). When matlab crashes, it throws an error in the console (Segmentation fault). 

What is going on here? How can I fix this?   :confused:
Thanks for you time.

---

### Post by 243kof on 2009-08-04
> **IstariAsuka said:**
> 
First, I can start matlab from the console. Seems to start up and work great. However, if I try to start it via the gui it starts the splashscreen but then dies. Moreover, the "matlab" and "matlab_helper" processes are still there, and have to be killed manually.  



You can edit the properties of the gui launcher and add the parameter "-desktop" at the end of the "command" field. It worked for me. As for your other problems, I'm afraid I can't help you. :(

PS. On a slightly irrelevant issue, do you run Matlab with desktop effects on? If yes, have you ever noticed your matlab windows just disappearing? This bug is driving me crazy :)

---

### Post by IstariAsuka on 2009-08-04
Looking through the internets, I eventually found on matlab's website that newer versions of matlab no longer include the jre.cfg file it was complaining about, yet comsol requires this file to exist for handshaking. [The site](http://www.mathworks.com/support/solutions/en/data/1-85KKQH/index.html?product=ML&solution=1-85KKQH) advised I create an empty jre.cfg file in the appropriate directory. I did so, but matlab now couldn't find java. So I set the MATLAB_JAVA environment variable to point to my JRE (1.6).

Trying to run it after doing all that, instead of comsol/matlab just dying when it attempts to do something, it instead seems to get slightly further before matlab once again crashes. Now, however, it pops up a window with a dump of the crash, which is as follows:

```
Configuration:
  MATLAB Version:   7.7.0.471 (R2008b)
  MATLAB License:   XXXXXX
  Operating System: Linux 2.6.31-rc4-adl #1 SMP Wed Jul 29 19:41:36 MST 2009 i686
  GNU C Library:    2.9 stable
  Processor ID:     x86 Family 15 Model 3 Stepping 3, AuthenticAMD
  Virtual Machine:  Java 1.6.0_14 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode, sharing
  Default Encoding:  US-ASCII

Fault Count: 1

Register State:
  eax = ae2fd0e8   ebx = 09f71bf0
  ecx = 09f71bf8   edx = ae2fd100
  esi = 00000000   edi = 00000002
  ebp = ae2fd120   esp = ae2fd098
  eip = a86499b1   flg = 00010246

Stack Trace:
  [0] mllapack.so:dlange_~(0xa888c66c "MG", 0xae2fd5a8, 0xae2fd5ac, 0x09f71bf8) + 209 bytes
  [1] mllapack.so:dgesvd_~(0xae2fd5e4, 0xae2fd5e8, 0xae2fd5a8, 0xae2fd5ac) + 816 bytes
  [2] libflarray.so:flarray::svd(char, char, Array<double, 2u>&, Array<double, 2u>&, Array<double, 1u>&, Array<double, 2u>&, int)~(0xadb78978, 0xa990fce4 "&#65533;*k", 0xa93761b9, 78) + 1289 bytes
  [3] libflarray.so:flarray::svd(Array<double, 2u>&, Array<double, 1u>&, int)~(0xae2fd694, 0xae2fd6ec, 3, 0xb75f5140) + 201 bytes
  [4] libflarray.so:flarray::rank(Array<double, 2u> const&, double, double&)~(0xa990fce4 "&#65533;*k", 0xa9375d7c, 0xae2fd7c0, 0xe91b0b71) + 248 bytes
  [5] libflarray.so:flarray::rank(Array<double, 2u> const&, double)~(0xae2fd7c0, 0xe91b0b71, 0x3dd07e1f, 0xab8fd42e) + 46 bytes
  [6] libflgeom.so:MfdBase::isLinear(double) const~(0xaa9d533c, 0xaa0e72a0, 0x09c85508 "4Rx&#65533;)", 0xe91b0b71) + 1469 bytes
  [7] libflgeom.so:BezierMfd::isLinear(double) const~(0x09c85478, 0xe91b0b71, 0x3dd07e1f, 0xaa785234) + 180 bytes
  [8] libflgeom.so:virtual thunk to BezierMfd::isLinear(double) const~(0x09c85508 "4Rx&#65533;)", 0xe91b0b71, 0x3dd07e1f, 4) + 49 bytes
  [9] libflgeom.so:Geom2::isEntityLinear(int, int) const~(0x09c9ffe8, 1, 0, 0xab906c9a) + 169 bytes
  [10] libflxmesh.so:_ZN18LenoirGeomMeshInfoC9EN7flboost10shared_ptrI4GeomEENS1_IN6flmesh8MeshBaseEEE~(0x09f70ef8, 0xae2fda38, 0xae2fda40, 0xac626580) + 354 bytes
  [11] libflxmesh.so:LenoirGeomMeshInfo::LenoirGeomMeshInfo(flboost::shared_ptr<Geom>, flboost::shared_ptr<flmesh::MeshBase>)~(0x09f70ef8, 0xae2fda38, 0xae2fda40, 0xadbe23b8) + 33 bytes
  [12] libflxmesh.so:GeomData::getLenoirAdjMeshPart(int, int, int)~(0xae2fdb94, 0xadbe23b8, 2, 0) + 259 bytes
  [13] libflxmesh.so:MEGrp::calcBmeInd(MultiTree<GeomData, 1>, MultiTree<int, 1>, int, std::vector<int, std::allocator<int> > const&, std::vector<int, std::allocator<int> > const&, std::vector<double, std::allocator<double> > const&, std::vector<std::vector<double, std::allocator<double> >, std::allocator<std::vector<double, std::allocator<double> > > >&)~(0x09f711c0, 0xae2fe694, 0xae2fe69c, 0) + 2177 bytes
  [14] libflxmesh.so:XModel::meshExtend(flutil::RunInfo&, flbase::Prop&)~(0xad4f5f68, 0xadb4c9d0, 0xad210b58, 0xadbe0ef0) + 12774 bytes
  [15] libflxmesh.so:Xmesh::meshExtend(flutil::RunInfo&, flbase::Prop&)~(0xadbe0ef0, 0xadb4c9d0, 0xad210b58, 0xae2fec08) + 126 bytes
  [16] libfljni.so:Java_com_femlab_xmesh_Xmesh_meshExtend~(0xad318910, 0xae2fee48, 0xae2fee44, 0xae2fee40) + 756 bytes
  [17] 0xafa4cf4d(0, 0xafa4b339, 0x8029a080, 0x8029a060)
  [18] 0xafa45fcd(0x8029a060, 0x80299ef0, 0x8028f1e0, 0xae2fee80)
  [19] 0xafa45fcd(0x8029a060, 0xae2feeac, 0x904f119a "&#65533;*", 0xae2feedc)
  [20] 0xafa45fcd(0, 0, 0x8029a0b8, 0xae2feee0)
  [21] 0xafa464a9(0x8029a200, 0xae2fef0c, 0x9072483c "&#65533;2", 0xae2fef40)
  [22] 0xafa464a9(0, 0, 0, 0x7fc8daa8)
  [23] 0xafa432cc(0xae2fefc0, 0xae2ff194, 10, 0x907248c0)
  [24] libjvm.so:0xb1cb4560(0xae2ff190, 0xae2ff058, 0xae2ff0c0, 0xad318800)
  [25] libjvm.so:0xb1dc7f58(0xb1cb43d0, 0xae2ff190, 0xae2ff058, 0xae2ff0c0)
  [26] libjvm.so:0xb1cb3d67(0xae2ff190, 0xae3587d4, 0xb23409b0, 0xb2340c24)
  [27] libjvm.so:0xb1cb3e1a(0xae2ff190, 0xae3587d0, 0xae3587d4, 0xb23409b0)
  [28] libjvm.so:0xb1d31135(0xad318800, 0xad318800, 0, 0)
  [29] libjvm.so:0xb1e6b43e(0xad318800, 1, 0, 0)
  [30] libjvm.so:0xb1dc93fe(0xad318800, 0xae2ffb90, 0xae2ffb90, 0xae2ffb90)
  [31] libpthread.so.0:0xb75fe4ff(0xae2ffb90, 0, 0, 0)
```

---

### Post by barhey on 2009-08-14
I have exactly the same problem.. very disturbing!

If you find any solution, let me know.


I have tried the same things (renaming jre to jre1.6.0_0 and creating jre.cfg with 1.6.0_0 written inside) with the same conclusions.

---

### Post by nutsy.ben on 2010-04-01
Well, One year old and no more ideas ?

I have to admit that I face the same problem.
I run Matlab + COMSOL on 3 different PC, all with Ubuntu 9.04.

On two of them I have Matlab 2008a and on the last the 2009.
I also run different architecture 64 and 32 bits .... 

PC 1         MATLAB2008a             AMD64         COMSOL35        Works
PC 2         MATLAB2008a             Intel            COMSOL35        **Segmentation Fault*
PC 3         MATLAB2009a             AMD64         COMSOL35        Crash when application starts

The only reason why the PC1 might work ??? the ATI graphic card ????....
If I had the solution I would show off .... but I don't 
help is welcome as this issue is more than 4 years old and still not fixed .... :s

---

