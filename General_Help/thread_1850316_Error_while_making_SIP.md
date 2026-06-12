---
title: "Error while making SIP"
date: 2011-09-26
forum: General Help
---

### Post by anshulfy on 2011-09-26
Hi,
I am trying to install scilab image processing toolbox. While making it i am getting the following error. I am new to linux, don't know what to do. Please help me.

```

/usr/bin/ld: warning: libsciparameters.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscicore.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libscicall_scilab.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscidouble.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciboolean.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciintersci.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libscilocalization.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscispecial_functions.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscistatistics.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscitime.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libsciwindows_tools.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscisparse.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciio.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscipolynomials.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscicacsd.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libmx.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libmat.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscidifferential_equations.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libmex.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscidata_structures.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libsciinteger.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscilinear_algebra.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscidynamic_link.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscicompletion.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscifunctions.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscihdf5.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscipvm.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscifftw.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscigraphics.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscihashtable.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscigui.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscirenderer.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libscidoublylinkedlist.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscigraphic_export.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libsciconsole.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscishell.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libscihistory_manager.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libsciaction_binding.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libsciscinotes.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciui_data.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscijvm.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscidynamiclibrary.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscihistory_browser.so.5, needed  by /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscicommons.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscitclsci.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscifileio.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscistring.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscielementary_functions.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciarnoldi.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libsciapi_scilab.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscilibst.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libscimalloc.so.5, needed by /usr/lib/scilab/libscilab.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld:  warning: libscioutput_stream.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
/usr/bin/ld: warning: libscihdf5-forceload.so.5, needed by  /usr/lib/scilab/libscilab.so, not found (try using -rpath or  -rpath-link)
../src/.libs/libsip.so: undefined reference to `stack_'
../src/.libs/libsip.so: undefined reference to `vartype_'
../src/.libs/libsip.so: undefined reference to `createlistvarfromptr_'
../src/.libs/libsip.so: undefined reference to `getrhsvar_'
../src/.libs/libsip.so: undefined reference to `createvarfromptr_'
../src/.libs/libsip.so: undefined reference to `get_optionals'
../src/.libs/libsip.so: undefined reference to `createlistcvarfromptr_'
../src/.libs/libsip.so: undefined reference to `checklhs_'
../src/.libs/libsip.so: undefined reference to `numopt_'
../src/.libs/libsip.so: undefined reference to `Scierror'
../src/.libs/libsip.so: undefined reference to `checkrhs_'
../src/.libs/libsip.so: undefined reference to `getlistrhscvar_'
../src/.libs/libsip.so: undefined reference to `getlistrhsvar_'
../src/.libs/libsip.so: undefined reference to `com_'
../src/.libs/libsip.so: undefined reference to `intersci_'
../src/.libs/libsip.so: undefined reference to `FreeRhsSVar'
../src/.libs/libsip.so: undefined reference to `createvar_'
../src/.libs/libsip.so: undefined reference to `check_length'
../src/.libs/libsip.so: undefined reference to `sciprint'
../src/.libs/libsip.so: undefined reference to `sci_gateway'
collect2: ld returned 1 exit status
make[1]: *** [sip_link_test] Error 1

```

Thanks,
Anshul

---

### Post by gallina on 2011-12-05
Hi,

I have no solution, but have the same problem.
I tried to uninstall and install ImageMagick, animal... all the last version.
No way, when i execute make install from sip, I have the same error.

Any suggestion?

---

### Post by anshulfy on 2011-12-05
Hi,

I wrote a mail to the author of the code, regarding the issue. He is looking into it. Till now he did not informed me about any progress.
--
Anshul.

---

### Post by kali26 on 2012-01-20
I just got all the stuff , scilab, SIP, ImageMagick, Animal. Compilation was OK, had to sudo make installs to get libraries in place and finally run /sbin/ldconfig (also as superuser). SIP is visible in the toolbox menu BUT invoking the demonstration freezes scilab totally in the first imshow ...

---

