---
title: "mapreduce"
date: 2011-12-20
forum: General Help
---

### Post by chandrashekar1945 on 2011-12-20
11/12/20 14:44:44 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
11/12/20 14:44:44 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
11/12/20 14:44:44 WARN mapred.JobClient: No job jar file set.  User classes may not be found. See JobConf(Class) or JobConf#setJar(String).
11/12/20 14:44:44 INFO mapred.JobClient: Cleaning up the staging area file:/tmp/hadoop-dev/mapred/staging/dev-783735819/.staging/job_local_0001
Exception in thread "main" org.apache.hadoop.mapred.FileAlreadyExistsException: Output directory file:/grid/testdata/test.out already exists
    at org.apache.hadoop.mapred.FileOutputFormat.checkOutputSpecs(FileOutputFormat.java:117)
    at org.apache.hadoop.mapred.JobClient$2.run(JobClient.java:874)
    at org.apache.hadoop.mapred.JobClient$2.run(JobClient.java:833)
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.security.auth.Subject.doAs(Subject.java:396)
    at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1127)
    at org.apache.hadoop.mapred.JobClient.submitJobInternal(JobClient.java:833)
    at org.apache.hadoop.mapred.JobClient.submitJob(JobClient.java:807)
    at org.apache.hadoop.mapred.JobClient.runJob(JobClient.java:1242)
    at MapReduce.run(MapReduce.java:62)
    at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:65)
    at MapReduce.main(MapReduce.java:67)

---

