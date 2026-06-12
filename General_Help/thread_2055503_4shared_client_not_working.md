---
title: "4shared client not working"
date: 2012-09-09
forum: General Help
---

### Post by LK_gandalf_ on 2012-09-09
Hi all, I am trying out 4shared because it gives 15gb free, webdav options, and so on. It provides a linux client in .deb (desktop4shared-1.3_1-all.deb), I can succesfully login but then if I try, for example, to create a folder, it stucks forever on a loading screen with "Loading, please wait" and I can only close the application. If I try to upload a file, even a small fil, it says "Files you try to upload are greater then file size limit".
I'm using Kubuntu 12.04 64bit with the latest java installed.
Do you have any clue on how to solve this? I mailed the support service but still haven't got any answer.
Thanks

Here the code I got from the terminal when it stucks:

```
]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at com.pmstation.shared.account.presentation.SyncWWWRedirectFilter.doFilter(SyncWWWRedirectFilter.java:49) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at com.pmstation.shared.server.presentation.HttpsFilter.doFilter(HttpsFilter.java:49) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:83) ~[na:na]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:76) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at com.pmstation.shared.server.IOExceptionSuppressorFilter.doFilter(IOExceptionSuppressorFilter.java:22) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at com.pmstation.shared.server.presentation.AllTopFilter.computeAndCall(AllTopFilter.java:483) ~[na:na]
        at com.pmstation.shared.server.presentation.AllTopFilter.reqImpl(AllTopFilter.java:448) ~[na:na]
        at com.pmstation.shared.server.presentation.AllTopFilter.doFilterCorrectedAddr(AllTopFilter.java:315) ~[na:na]
        at com.pmstation.shared.server.presentation.AllTopFilter.doFilter(AllTopFilter.java:168) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:235) ~[na:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:206) ~[na:na]
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:233) ~[na:na]
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:191) ~[na:na]
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:127) ~[na:na]
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102) ~[na:na]
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109) ~[na:na]
        at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:298) ~[na:na]
        at org.apache.coyote.http11.Http11AprProcessor.process(Http11AprProcessor.java:864) ~[na:na]
        at org.apache.coyote.http11.Http11AprProtocol$Http11ConnectionHandler.process(Http11AprProtocol.java:579) ~[na:na]
        at org.apache.tomcat.util.net.AprEndpoint$Worker.run(AprEndpoint.java:1665) ~[na:na]
19:12:07 [Thread-15] ERROR common.GlobalExceptionHandler - Uncaught exception in thread [Thread-15] : Cannot get property 'userObject' on null object
java.lang.NullPointerException: Cannot get property 'userObject' on null object
        at DesktopController$_closure19_closure52_closure53_closure54.doCall(DesktopController.groovy:254) ~[desktop4shared.jar:na]

```

---

### Post by LK_gandalf_ on 2012-09-27
any idea?

---

