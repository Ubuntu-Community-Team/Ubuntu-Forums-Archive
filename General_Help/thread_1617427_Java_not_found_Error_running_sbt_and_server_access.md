---
title: "Java not found? Error running sbt and server access error"
date: 2010-11-09
forum: General Help
---

### Post by kv_flock on 2010-11-09
[SIZE=3]I'm trying to build FlockDB, but when I try to run "sbt update package-dist" I run into the following errors, which I don't understand. I know I have java installed (and which java returns a directory), but for some reason it says "Cannot run program "javac": java.io.IOException: error=2, No such file or directory" Is there something I'm missing???

An unrelated question is how do I get .poms if the server is down? In some cases, they seem to download successfully, but especially for Atlassian, it seems to be flaking out and I don't know where else to get these (or even what a .pom really is)... Thanks for any help!!
[/SIZE]

root@kv-VirtualBox:/usr/bin/twitter-flockdb-6918136# sbt clean update package-dist
[info] Standard project rules 0.7.10 loaded (2010-10-12).
[warn] No .svnrepo file; no svn repo will be configured.
[info] Building project flockdb 1.4.6-SNAPSHOT against Scala 2.7.7
[info]    using FlockDBProject with sbt 0.7.4 and Scala 2.7.7
[info] 
[info] == clean-dist ==
[info] == clean-dist ==
[info] 
[info] == clean-thrift ==
[info] Deleting directory /usr/bin/twitter-flockdb-6918136/target/gen-java
[info] Deleting directory /usr/bin/twitter-flockdb-6918136/target/gen-rb
[info] == clean-thrift ==
[info] 
[info] == clean ==
[info] Deleting directory /usr/bin/twitter-flockdb-6918136/target
[info] == clean ==
[success] Successful.
[info] 
[info] Total time: 0 s, completed Nov 9, 2010 10:29:52 AM
[info] 
[info] == update ==
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.pom
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.pom
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.jar
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.pom
[error] Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.jar
[info] 
[error] :: problems summary ::
[error] :::: ERRORS
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.pom
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/com/twitter/xrayspecs/1.0.7/xrayspecs-1.0.7.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.pom
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/org/scala-tools/vscaladoc/1.1-md-3/vscaladoc-1.1-md-3.jar
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.pom
[error]     Server access Error: Connection timed out url=https://m2proxy.atlassian.com/repository/public/thrift/libthrift/0.2.0-twitter-1/libthrift-0.2.0-twitter-1.jar
[info] 
[info] :: USE VERBOSE OR DEBUG MESSAGE LEVEL FOR MORE DETAILS
[info] :: retrieving :: com.twitter#flockdb [sync]
[info]     confs: [compile, runtime, test, provided, system, optional, sources, javadoc]
[info]     0 artifacts copied, 41 already retrieved (0kB/81ms)
[info] == update ==
[success] Successful.
[info] 
[info] Total time: 145 s, completed Nov 9, 2010 10:32:17 AM
[info] 
[info] == compile-thrift-java ==
[info] == compile-thrift-java ==
[info] 
[info] == compile-thrift-ruby ==
[info] == compile-thrift-ruby ==
[info] 
[info] == compile ==
[info]   Source analysis: 64 new/modified, 0 indirectly invalidated, 0 removed.
[info] Compiling main sources...
java.io.IOException: Cannot run program "javac": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at sbt.SimpleProcessBuilder.run(ProcessImpl.scala:381)
    at sbt.AbstractProcessBuilder.run(ProcessImpl.scala:132)
    at sbt.AbstractProcessBuilder$$anonfun$runBuffered$1.apply(ProcessImpl.scala:165)
    at sbt.AbstractProcessBuilder$$anonfun$runBuffered$1.apply(ProcessImpl.scala:165)
    at sbt.BufferedLogger.bufferAll(Logger.scala:179)
    at sbt.AbstractProcessBuilder.runBuffered(ProcessImpl.scala:165)
    at sbt.AbstractProcessBuilder.$bang(ProcessImpl.scala:160)
    at sbt.Compile.externalJavac$1(Compile.scala:93)
    at sbt.Compile$$anonfun$forkJavac$2.apply(Compile.scala:94)
    at sbt.Compile$$anonfun$forkJavac$2.apply(Compile.scala:94)
    at sbt.WithArgumentFile$$anonfun$withArgumentFile$1.apply(Compile.scala:116)
    at sbt.WithArgumentFile$$anonfun$withArgumentFile$1.apply(Compile.scala:113)
    at xsbt.FileUtilities$.withTemporaryDirectory(FileUtilities.scala:169)
    at sbt.WithArgumentFile$class.withArgumentFile(Compile.scala:113)
    at sbt.Compile.withArgumentFile(Compile.scala:71)
    at sbt.Compile.forkJavac(Compile.scala:94)
    at sbt.Compile.processJava(Compile.scala:86)
    at sbt.CompilerCore$$anonfun$2.apply(Compile.scala:28)
    at sbt.CompilerCore$$anonfun$2.apply(Compile.scala:28)
    at sbt.CompilerCore$$anonfun$process$1$1.apply(Compile.scala:22)
    at sbt.CompilerCore$$anonfun$process$1$1.apply(Compile.scala:22)
    at sbt.CompilerCore$$anonfun$doCompile$3.apply(Compile.scala:45)
    at sbt.CompilerCore$$anonfun$doCompile$3.apply(Compile.scala:42)
    at scala.Option.orElse(Option.scala:102)
    at sbt.CompilerCore.doCompile(Compile.scala:41)
    at sbt.CompilerCore.apply(Compile.scala:29)
    at sbt.AbstractCompileConditional.run$1(Conditional.scala:341)
    at sbt.AbstractCompileConditional$$anonfun$3.apply(Conditional.scala:344)
    at sbt.AbstractCompileConditional$$anonfun$3.apply(Conditional.scala:344)
    at sbt.classfile.Analyze$.apply(Analyze.scala:110)
    at sbt.AbstractCompileConditional.execute(Conditional.scala:344)
    at sbt.Conditional$class.run(Conditional.scala:43)
    at sbt.AbstractCompileConditional.run(Conditional.scala:231)
    at sbt.BasicScalaProject.sbt$BasicScalaProject$$doCompile(DefaultProject.scala:259)
    at sbt.BasicScalaProject$$anonfun$compileAction$1.apply(DefaultProject.scala:273)
    at sbt.BasicScalaProject$$anonfun$compileAction$1.apply(DefaultProject.scala:273)
    at sbt.TaskManager$Task.invoke(TaskManager.scala:62)
    at sbt.impl.RunTask.doRun$1(RunTask.scala:77)
    at sbt.impl.RunTask.runTask(RunTask.scala:85)
    at sbt.impl.RunTask.sbt$impl$RunTask$$runIfNotRoot(RunTask.scala:60)
    at sbt.impl.RunTask$$anonfun$runTasksExceptRoot$2.apply(RunTask.scala:48)
    at sbt.impl.RunTask$$anonfun$runTasksExceptRoot$2.apply(RunTask.scala:48)
    at sbt.Distributor$Run$Worker$$anonfun$2.apply(ParallelRunner.scala:131)
    at sbt.Distributor$Run$Worker$$anonfun$2.apply(ParallelRunner.scala:131)
    at sbt.Control$.trapUnit(Control.scala:19)
    at sbt.Distributor$Run$Worker.run(ParallelRunner.scala:131)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    at sbt.SimpleProcessBuilder.run(ProcessImpl.scala:381)
    at sbt.AbstractProcessBuilder.run(ProcessImpl.scala:132)
    at sbt.AbstractProcessBuilder$$anonfun$runBuffered$1.apply(ProcessImpl.scala:165)
    at sbt.AbstractProcessBuilder$$anonfun$runBuffered$1.apply(ProcessImpl.scala:165)
    at sbt.BufferedLogger.bufferAll(Logger.scala:179)
    at sbt.AbstractProcessBuilder.runBuffered(ProcessImpl.scala:165)
    at sbt.AbstractProcessBuilder.$bang(ProcessImpl.scala:160)
    at sbt.Compile.externalJavac$1(Compile.scala:93)
    at sbt.Compile$$anonfun$forkJavac$2.apply(Compile.scala:94)
    at sbt.Compile$$anonfun$forkJavac$2.apply(Compile.scala:94)
    at sbt.WithArgumentFile$$anonfun$withArgumentFile$1.apply(Compile.scala:116)
    at sbt.WithArgumentFile$$anonfun$withArgumentFile$1.apply(Compile.scala:113)
    at xsbt.FileUtilities$.withTemporaryDirectory(FileUtilities.scala:169)
    at sbt.WithArgumentFile$class.withArgumentFile(Compile.scala:113)
    at sbt.Compile.withArgumentFile(Compile.scala:71)
    at sbt.Compile.forkJavac(Compile.scala:94)
    at sbt.Compile.processJava(Compile.scala:86)
    at sbt.CompilerCore$$anonfun$2.apply(Compile.scala:28)
    at sbt.CompilerCore$$anonfun$2.apply(Compile.scala:28)
    at sbt.CompilerCore$$anonfun$process$1$1.apply(Compile.scala:22)
    at sbt.CompilerCore$$anonfun$process$1$1.apply(Compile.scala:22)
    at sbt.CompilerCore$$anonfun$doCompile$3.apply(Compile.scala:45)
    at sbt.CompilerCore$$anonfun$doCompile$3.apply(Compile.scala:42)
    at scala.Option.orElse(Option.scala:102)
    at sbt.CompilerCore.doCompile(Compile.scala:41)
    at sbt.CompilerCore.apply(Compile.scala:29)
    at sbt.AbstractCompileConditional.run$1(Conditional.scala:341)
    at sbt.AbstractCompileConditional$$anonfun$3.apply(Conditional.scala:344)
    at sbt.AbstractCompileConditional$$anonfun$3.apply(Conditional.scala:344)
    at sbt.classfile.Analyze$.apply(Analyze.scala:110)
    at sbt.AbstractCompileConditional.execute(Conditional.scala:344)
    at sbt.Conditional$class.run(Conditional.scala:43)
    at sbt.AbstractCompileConditional.run(Conditional.scala:231)
    at sbt.BasicScalaProject.sbt$BasicScalaProject$$doCompile(DefaultProject.scala:259)
    at sbt.BasicScalaProject$$anonfun$compileAction$1.apply(DefaultProject.scala:273)
    at sbt.BasicScalaProject$$anonfun$compileAction$1.apply(DefaultProject.scala:273)
    at sbt.TaskManager$Task.invoke(TaskManager.scala:62)
    at sbt.impl.RunTask.doRun$1(RunTask.scala:77)
    at sbt.impl.RunTask.runTask(RunTask.scala:85)
    at sbt.impl.RunTask.sbt$impl$RunTask$$runIfNotRoot(RunTask.scala:60)
    at sbt.impl.RunTask$$anonfun$runTasksExceptRoot$2.apply(RunTask.scala:48)
    at sbt.impl.RunTask$$anonfun$runTasksExceptRoot$2.apply(RunTask.scala:48)
    at sbt.Distributor$Run$Worker$$anonfun$2.apply(ParallelRunner.scala:131)
    at sbt.Distributor$Run$Worker$$anonfun$2.apply(ParallelRunner.scala:131)
    at sbt.Control$.trapUnit(Control.scala:19)
    at sbt.Distributor$Run$Worker.run(ParallelRunner.scala:131)
[info] == compile ==
[info] 
[info] == copy-resources ==
[info] == copy-resources ==
[info] 
[info] == copy-test-resources ==
[info] == copy-test-resources ==
[info] 
[info] == write-build-properties ==
[info] == write-build-properties ==
[error] Error running compile: java.io.IOException: Cannot run program "javac": java.io.IOException: error=2, No such file or directory
[info] 
[info] Total time: 1 s, completed Nov 9, 2010 10:32:18 AM
[info] 
[info] Total session time: 147 s, completed Nov 9, 2010 10:32:18 AM
[error] Error during build.

---

