HYPRIOTOS=./hypriotos-rpi-v1.7.1.img.zip
DEVICE=/dev/sda

HOSTNAME:=RPiSen2
USER:=montreal
GECOS:=montreal
HOME:=/home/montreal
TIMESERVER:=0.de.pool.ntp.org
IMAGE:=r3r57/montreal:latest-multiarch
NSQ_IMAGE:=r3r57/nsq-multiarch:v1.0.0-compat
SWARM_TOKEN:=SWMTKN-1-0w2o6fq47z2lcxxau8l7e4rpwxjf4xknhkirzvs371sf6ck826-1nyfr7axrno77frdqseq0l24w
SWARM_LEADER_IP:=192.168.178.29:2377
DEVICE_ID:=${HOSTNAME}
BUILDING:=L9
ROOM:=00.01
ARCHITECTURE:=arm

flash_sd:
	-sed -e "s|{USER}|${USER}|g" cloud-init.template.yml > cloud-init.yml
	-sed -i -e "s|{GECOS}|${GECOS}|g" cloud-init.yml
	-sed -i -e "s|{HOME}|${HOME}|g" cloud-init.yml
	-sed -i -e "s|{HOSTNAME}|${HOSTNAME}|g" cloud-init.yml
	-sed -i -e "s|{TIMESERVER}|${TIMESERVER}|g" cloud-init.yml
	-sed -i -e "s|{IMAGE}|${IMAGE}|g" cloud-init.yml
	-sed -i -e "s|{NSQ_IMAGE}|${NSQ_IMAGE}|g" cloud-init.yml
	-sed -i -e "s|{SWARM_TOKEN}|${SWARM_TOKEN}|g" cloud-init.yml
	-sed -i -e "s|{SWARM_LEADER_IP}|${SWARM_LEADER_IP}|g" cloud-init.yml
	-sed -i -e "s|{DEVICE_ID}|${DEVICE_ID}|g" cloud-init.yml
	-sed -i -e "s|{BUILDING}|${BUILDING}|g" cloud-init.yml
	-sed -i -e "s|{ROOM}|${ROOM}|g" cloud-init.yml
	-sed -i -e "s|{ARCHITECTURE}|${ARCHITECTURE}|g" cloud-init.yml
	-cat cloud-init.yml
	-curl -sLo ./flash https://raw.githubusercontent.com/hypriot/flash/master/Linux/flash
	-chmod +x ./flash
	-./flash -u cloud-init.yml -d ${DEVICE} ${HYPRIOTOS}
	-rm -f ./flash ./cloud-init.yml
