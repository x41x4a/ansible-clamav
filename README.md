# ansible-clamav
This is an Ansible role I've created for deploying ClamAV in a Linux server environment.  I pulled it out of a larger set of roles, but it should work standalone as well.

It includes two tasks, install and cron_add.  They are pretty self-explanatory.

Install makes sure the latest version of the clamav scanner and freshclam updater are installed, copies over an 'agent' freshclam.conf, and ensures our desired log directory is present.  We are using a private local mirror to serve out signatures internally so our freshclam configuration is set up accordingly.

The cron_add task configures cron jobs for both scans (Tuesday & Thursday @ 10:30PM) and signature updates (nightly @ 10PM).

There is a third task not included by default, cron_remove.  It can be used to remove the scan and update jobs from system crontabs.  To do this, add an include statement for cron_remove.yml in tasks/main.yml
