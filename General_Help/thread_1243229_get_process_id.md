---
title: "get process id"
date: 2009-08-18
forum: General Help
---

### Post by premabodh on 2009-08-18
Hi All,

I have a shell script file that is run by a schedular at every 3 minutes. The shell script code is:

cd /opt/JAR

/opt/ProjectTools/JDK1.6/jdk1.5.0_16/bin/java -jar Trip.jar

Now whenever Trip.jar runs there must be a process Id for it. Please let me know how to get this process id of that in same Shell Script code.

Is it possible that it has something like this:
int/var $pid = /opt/ProjectTools/JDK1.6/jdk1.5.0_16/bin/java -jar Trip.jar

where pid is the process Id.

because what exactly is happening is that due to some problem with the jar file created the application hangs and every 3 mins new process Id is formed and as day ends we see many java processes running that slows down the syatem and we have to manually kill those processes.

I cannot have killall query at scheduled basis as there are many other schedulars running diffrent java applications.

Please help me out.

Thanks and Regards,
Vikash Anand.
:popcorn:

---

### Post by nikhilk on 2009-08-18
The PID of the latest process started from a bash script is saved in the special variable $!

So you can get the PID as show below
```

cd /opt/JAR
/opt/ProjectTools/JDK1.6/jdk1.5.0_16/bin/java -jar Trip.jar &
myPID=$!

```

---

### Post by geirha on 2009-08-18
Start the command in the background (& behind the command runs it in the background), then read $!. $! contains the pid of the most recently executed background command. 

So you can do something like this for instance:
```

command & pid=$!
sleep 60                # sleep for 60 seconds
if kill -0 $pid; then   # Check if it is still running
  echo "command still running after 1 minute. Killing it..."
  kill $pid
fi

```

---

### Post by premabodh on 2009-08-18
I found solution to the problem:

cd /opt/processTest

/opt/JDK/jdk1.5.0_16/bin/java StringTest

echo $$

The "$$" gives the process Id.

:lolflag:

---

### Post by nikhilk on 2009-08-18
> **premabodh said:**
> I found solution to the problem:

cd /opt/processTest

/opt/JDK/jdk1.5.0_16/bin/java StringTest

echo $$

The "$$" gives the process Id.

Just to clarify, $$ gives the PID of the script itself and not the Java process launched from it.

Killing the script itself may work but I think there are no guarantees that all process launched from a script will be terminated when the script itself is terminated unless you use trap or some such mechanism to ensure termination of all child processes.

---

### Post by riazrahaman on 2009-08-18
other way would be

install htop

sudo apt-get install htop

run htop

htop, and monitor the new processes that are created.

This may really not be a good way.

---

### Post by slakkie on 2009-08-18
```


PID_FILE=/path/to/pid/file
PID=$(cat $PID)

check_pid() {
  ps -p $1 &>/dev/null
}

check_pid $PID
if [ $? -eq 0 ] ; then
    kill $PID
    sleep 5
    check_pid $PID && kill -9 $PID
fi

# Start APP
cd /path/to/app
./app.sh
RC=$?
PID=$!

echo $PID > $PID_FILE
exit $RC

```

This way, everytime you run it, you have a pid file of the previous run and it will kill the previous run when needed.

---

