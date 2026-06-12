---
title: "I keep getting the following error in NetBeans"
date: 2012-05-12
forum: General Help
---

### Post by oshirowanen on 2012-05-12
I keep getting the following error in NetBeans

    java.lang.IllegalStateException: Cannot find an HtmlParser implementation for HTML5

Followed by

    	at org.netbeans.editor.ext.html.parser.api.SyntaxAnalyzerResult.findParser(Unknown Source)
    	at org.netbeans.editor.ext.html.parser.api.SyntaxAnalyzerResult.doParseHtml(Unknown Source)
    	at org.netbeans.editor.ext.html.parser.api.SyntaxAnalyzerResult.parseHtml(Unknown Source)
    	at org.netbeans.modules.html.editor.api.gsf.HtmlParserResult.root(Unknown Source)
    	at org.netbeans.modules.html.editor.gsf.HtmlStructureScanner.scan(Unknown Source)
    	at org.netbeans.modules.csl.navigation.ElementScanningTask$1.run(Unknown Source)
    	at org.netbeans.modules.csl.navigation.ElementScanningTask$1.run(Unknown Source)
    	at org.netbeans.modules.parsing.impl.TaskProcessor.callUserTask(Unknown Source)
    	at org.netbeans.modules.parsing.api.ParserManager$UserTaskAction.run(Unknown Source)
    	at org.netbeans.modules.parsing.api.ParserManager$UserTaskAction.run(Unknown Source)
    	at org.netbeans.modules.parsing.impl.TaskProcessor$2.call(Unknown Source)
    	at org.netbeans.modules.parsing.impl.TaskProcessor$2.call(Unknown Source)
    	at org.netbeans.modules.masterfs.filebasedfs.utils.FileChangedManager.priorityIO(Unknown Source)
    	at org.netbeans.modules.masterfs.providers.ProvidedExtensions.priorityIO(Unknown Source)
    	at org.netbeans.modules.parsing.impl.Utilities.runPriorityIO(Unknown Source)
    Caused: org.netbeans.modules.parsing.spi.ParseException
    	at org.netbeans.modules.parsing.impl.TaskProcessor.runUserTask(Unknown Source)
    [catch] at org.netbeans.modules.parsing.api.ParserManager.parse(Unknown Source)
    	at org.netbeans.modules.csl.navigation.ElementScanningTask.run(Unknown Source)
    	at org.netbeans.modules.csl.navigation.ClassMemberNavigatorSourceFactory$ProxyElementScanningTask.run(Unknown Source)
    	at org.netbeans.modules.csl.navigation.ClassMemberNavigatorSourceFactory$ProxyElementScanningTask.run(Unknown Source)
    	at org.netbeans.modules.parsing.impl.TaskProcessor.callParserResultTask(Unknown Source)
    	at org.netbeans.modules.parsing.impl.TaskProcessor$CompilationJob.run(Unknown Source)
    	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:471)
    	at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:334)
    	at java.util.concurrent.FutureTask.run(FutureTask.java:166)
    	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
    	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
    	at java.lang.Thread.run(Thread.java:679)

---

