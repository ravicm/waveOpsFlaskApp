#!/bin/bash
# description: A simple service script to start/stop/restart/status of python application
# TODO:
#   - Add logging related code
app_name=app
app_bin=$app_name.py
python_bin=`which python`

start() {
        echo -n "Starting $app_name server: "
	echo
        $python_bin $app_bin &
        ### Create the lock file ###
	mkdir lock
        touch lock/$app_name
        echo -n "Started  $app_name server successfuly"
	echo
}

stop() {
        echo -n "stopping $app_name server: "
	echo
	ps -ef|grep $app_bin|awk '{print $2}'|xargs -I{} kill -9 {}
        ### Create the lock file ###
        rm lock/$app_name
	rm -r lock
        echo -n "stopped $app_name server successfuly"
	echo
}

case "$1" in
  start)
        start
        ;;
  stop)
        stop
        ;;
  status)
        status FOO
        ;;
  restart)
        stop
        start
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart|status}"
        exit 1
esac
exit 0
