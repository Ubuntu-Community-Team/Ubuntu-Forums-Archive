---
title: "Irregular cron"
date: 2009-12-29
forum: General Help
---

### Post by dscheste on 2009-12-29
Dear Team,

Crontab is great. It can let you schedule anything and everything with any occurring schedule...


The problem I have at hand is tricky, I need to schedule regular hourly jobs that run at randomized time every hour.

I guess a solution might be to employ something like sleep and randomize the next execution time, but before I start reinventing the wheel,  I would like to ask if anybody has a suggestion for me here.

Thank you.

P.S. As an example, how do I program a job to run at 9:17, then 10:03, then some other obscure time on the 11th hour?

---

### Post by zey on 2009-12-29
If you wanna do something like that, I think you better to make a daemon instead of using cron. Make your own daemon and you can get anything you want.

---

### Post by DaithiF on 2009-12-29
Cron itself can't do something like this.  Short of writing your own daemon, you could get close to what you want using cron (though in a sort-of ugly fashion) like so:
1. create a cron job that runs a wrapper script every minute
2. this script runs your job, then figures out the (randomised) next run time and writes it to a marker file.
next time the script runs, it checks the current time vs. the values in the marker file -- if they don't match, it just exits, if it does match, then it runs the job / creates a new next runtime, etc...

sample implementation here:
```
marker_file='/home/you/.somejob-nextrun'

write_next_runtime()
{
    next_hour=$(date -d "1 hour" +%H)
    next_min=$(printf "%02d" $((RANDOM % 60)))
    echo "$next_hour $next_min" > $marker_file
}

run_job()
{
    echo "executing job"
    # do whatever stuff you need to do here
    write_next_runtime        # write out a maker file with next time to run
}

# if no marker file then just run
if [[ ! -e $marker_file ]]; then
    echo "Running job because no marker file found ($marker_file)"
    run_job
else
    read next_hour next_min < $marker_file
    now=$(date +%H:%M | cut -d':' --output-delimiter=' ' -f1,2)
    set -- $now
    this_hour=$1;this_min=$2

    if [[ $this_hour -eq $next_hour && $this_min -eq $this_min ]]; then
        echo "Running job because hour/min now ($this_hour:$this_min) matches next runtime of $next_hour:$next_min"
        run_job
    else
        echo "Not running job because hour/min now ($this_hour:$this_min) does not match next runtime of $next_hour:$next_min"
    fi
fi

```

---

