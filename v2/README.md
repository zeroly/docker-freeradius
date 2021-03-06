## Requirement
+ Docker 0.11

## Installation
1. Build image (as root)

	```bash
	$ docker pull catatnight/freeradius:latest
	$ wget https://raw.githubusercontent.com/catatnight/docker-freeradius/master/v2/manage.py
	$ chmod +x manage.py
	```

## Usage
1. Create container and manage it (as root)

	```bash
	$ ./manage.py [create|start|stop|restart|delete]
	```
	a) all remote clients are allowed, and access restriction could be made by firewall rules

	```bash
	$ ./manage.py -s radpass --mysql_server 1.2.3.4 -u test -p test create
	```
	b) authorized clients' been maintained in `nas` table

	```bash
	$ ./manage.py --readsqlclients --mysql_server 1.2.3.4 -u test -p test create
	```

## Note
+ `default_eap_type = mschapv2` in `eap.conf`
+ The following attributes are available in `radgroupcheck` table

	| id | groupname | attribute | op | value |
	|---|:---:|:---:|---|:---:|
	| 1 | VIP | Simultaneous-Use | := | 3 |
	| 2 | VIP | Max-Monthly-Traffic | := | 1024* |
	| 3 | VIP | Acct-Interim-Interval | := | 60 |
	*\*1024 Megabytes*

## Reference
+ [通过FreeRADIUS实现VPN流量控制功能 - WangYan Blog(Google cached page)](http://webcache.googleusercontent.com/search?q=cache:jLRYw52iUM0J:www.dannysite.com/blog/63/+&cd=1&hl=zh-CN&ct=clnk&gl=us)
+ TBD


