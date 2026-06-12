---
title: "Hudson/Maven: ArrayIndexOutOfBoundsException on site generation"
date: 2010-08-30
forum: General Help
---

### Post by andimeier on 2010-08-30
On a Ubuntu Lucid, I installed Hudson (1.352) and Maven (2.2.1-2). Works well, I am able to use maven in a Hudson job to build (compile) the Java project.

However, a site generation call with
  mvn site
(configured in a Hudson job) fails with the following message:

```
[WARNING] Deprecated API called - not org.apache.maven.doxia.sink.Sink instance and no SinkFactory available. Please update this plugin.
[INFO] ------------------------------------------------------------------------
[ERROR] FATAL ERROR
[INFO] ------------------------------------------------------------------------
[INFO] 1
[INFO] ------------------------------------------------------------------------
[INFO] Trace
java.lang.ArrayIndexOutOfBoundsException: 1
    at org.apache.maven.doxia.module.xhtml.XhtmlSink.tableCell(XhtmlSink.java:791)
    at org.apache.maven.doxia.module.xhtml.XhtmlSink.tableHeaderCell(XhtmlSink.java:777)
    at org.apache.maven.reporting.AbstractMavenReportRenderer.tableHeaderCell(AbstractMavenReportRenderer.java:267)
    at org.apache.maven.reporting.AbstractMavenReportRenderer.tableHeader(AbstractMavenReportRenderer.java:356)
    at org.apache.maven.report.projectinfo.TeamListReport$TeamListRenderer.renderBody(TeamListReport.java:160)
    at org.apache.maven.reporting.AbstractMavenReportRenderer.render(AbstractMavenReportRenderer.java:79)
    at org.apache.maven.report.projectinfo.TeamListReport.executeReport(TeamListReport.java:58)
    at org.apache.maven.reporting.AbstractMavenReport.generate(AbstractMavenReport.java:190)
    at org.apache.maven.reporting.AbstractMavenReport.generate(AbstractMavenReport.java:144)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
        [... more lines omitted...]

```In some forums I got the impression that the version of the maven site plugin may be a problem.

However, I am not sure where how I can check this.

I'm thankful for any hint.

TIA,
Andi

---

### Post by justmeatwork on 2010-10-28
Running into the same issue, is there a known solution or workaround for this issue?

---

### Post by t.n.a. on 2011-11-21
> **andimeier said:**
> In some forums I got the impression that the version of the maven site plugin may be a problem.

However, I am not sure where how I can check this.

It is, in fact, a problem with the Maven site plugin. A [bug]("http://jira.codehaus.org/browse/MPIR-195") has been reported and a workaround described.

In your top-level POM, you should explicitly set the site plugin version: e.g. 2.1.1 works, 2.2 does not. This is how you set the version under project/build/plugins in your POM:

```

			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-site-plugin</artifactId>
				<version>2.1.1</version>
			</plugin>


```

If this solves your problem, please append [SOLVED] to the thread name.

---

