---
title: "Why's maven2 pulling in gcj packages when I have openjdk?"
date: 2010-05-19
forum: General Help
---

### Post by yang on 2010-05-19
Why is 'apt-get install maven2' pulling in tons of gcj packages when I already have openjdk?

```

$ sudo aptitude install maven2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  ant{a} ant-gcj{a} ant-optional{a} ant-optional-gcj{a} antlr{a} bsh{a} fop{a} gcj-4.4-base{a} gcj-4.4-jre-lib{a} groovy{a} ivy{a} java-wrappers{a} 
  junit4{a} libantlr-java{a} libasm2-java{a} libasm3-java{a} libavalon-framework-java{a} libbackport-util-concurrent-java{a} libbatik-java{a} 
  libbsf-java{a} libclassworlds-java{a} libcommons-beanutils-java{a} libcommons-cli-java{a} libcommons-codec-java{a} libcommons-collections-java{a} 
  libcommons-collections3-java{a} libcommons-configuration-java{a} libcommons-digester-java{a} libcommons-httpclient-java{a} libcommons-io-java{a} 
  libcommons-jxpath-java{a} libcommons-lang-java{a} libcommons-logging-java{a} libcommons-net2-java{a} libcommons-validator-java{a} libdoxia-java{a} 
  libdoxia-sitetools-java{a} libexcalibur-logkit-java{a} libganymed-ssh2-java{a} libgcj-bc{a} libgcj-common{a} libgcj10{a} 
  libgeronimo-jms-1.1-spec-java{a} libgnuinet-java{a} libgnujaf-java{a} libgnumail-java{a} libgoogle-collections-java{a} libhamcrest-java{a} 
  libitext1-java{a} libjaxp1.3-java{a} libjdom1-java{a} libjline-java{a} libjsch-java{a} libjtidy-java{a} liblog4j1.2-java{a} libmaven-archiver-java{a} 
  libmaven-clean-plugin-java{a} libmaven-compiler-plugin-java{a} libmaven-dependency-tree-java{a} libmaven-file-management-java{a} 
  libmaven-filtering-java{a} libmaven-install-plugin-java{a} libmaven-jar-plugin-java{a} libmaven-plugin-tools-java{a} libmaven-reporting-impl-java{a} 
  libmaven-resources-plugin-java{a} libmaven-scm-java{a} libmaven-shade-plugin-java{a} libmaven-shared-io-java{a} libmaven2-core-java{a} 
  libmockobjects-java{a} libmodello-java{a} libnekohtml-java{a} libnetbeans-cvsclient-java{a} liboro-java{a} libplexus-ant-factory-java{a} 
  libplexus-archiver-java{a} libplexus-bsh-factory-java{a} libplexus-build-api-java{a} libplexus-cipher-java{a} libplexus-classworlds-java{a} 
  libplexus-compiler-api-java{a} libplexus-compiler-javac-java{a} libplexus-compiler-manager-java{a} libplexus-component-api-java{a} 
  libplexus-container-default-java{a} libplexus-containers-java{a} libplexus-digest-java{a} libplexus-i18n-java{a} libplexus-interactivity-api-java{a} 
  libplexus-interpolation-java{a} libplexus-io-java{a} libplexus-sec-dispatcher-java{a} libplexus-utils-java{a} libplexus-velocity-java{a} 
  libqdox-java{a} libregexp-java{a} libsaxon-java{a} libservlet2.4-java{a} libservlet2.5-java{a} libslf4j-java{a} libwagon-java{a} 
  libwerken.xpath-java{a} libxalan2-java{a} libxbean-java{a} libxerces2-java{a} libxml-commons-external-java{a} libxmlgraphics-commons-java{a} 
  libxpp3-java{a} libxstream-java{a} maven2 rhino{a} velocity{a} 
0 packages upgraded, 113 newly installed, 0 to remove and 0 not upgraded.
Need to get 70.6MB of archives. After unpacking 153MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

$ aptitude search openjdk
p   openjdk-6-dbg                                                          - Java runtime based on OpenJDK (debugging symbols)                               
p   openjdk-6-demo                                                         - Java runtime based on OpenJDK (demos and examples)                              
p   openjdk-6-doc                                                          - OpenJDK Development Kit (JDK) documentation                                     
i   openjdk-6-jdk                                                          - OpenJDK Development Kit (JDK)                                                   
i A openjdk-6-jre                                                          - OpenJDK Java runtime, using Hotspot JIT                                         
i A openjdk-6-jre-headless                                                 - OpenJDK Java runtime, using Hotspot JIT (headless)                              
i A openjdk-6-jre-lib                                                      - OpenJDK Java runtime (architecture independent libraries)                       
v   openjdk-6-jre-shark                                                    -                                                                                 
p   openjdk-6-jre-zero                                                     - Alternative JVM for OpenJDK, using Zero/Shark                                   
p   openjdk-6-source                                                       - OpenJDK Development Kit (JDK) source files

```

---

