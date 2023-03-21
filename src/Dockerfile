from ubuntu:22.04

run apt-get -y update
run apt-get -y install vim
run apt-get -y install curl
run apt-get -y install openjdk-8-jdk
run apt-get -y install openjdk-11-jdk
run apt-get -y install git
run apt-get -y install wget
run apt-get -y install unzip

run \
	curl https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip --output /tmp/android-command-line-tools.zip && \
	mkdir -p /usr/lib/android_sdk/cmdline-tools && \
	unzip /tmp/android-command-line-tools.zip -d /usr/lib/android_sdk/cmdline-tools && \
	rm /tmp/android-command-line-tools.zip && \
	mv /usr/lib/android_sdk/cmdline-tools/cmdline-tools /usr/lib/android_sdk/cmdline-tools/latest

env ANDROID_SDK_ROOT=/usr/lib/android_sdk
run ln -s ${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager /usr/bin/sdkmanager
run yes | sdkmanager --licenses

workdir /home

run git clone https://github.com/saneea/financisto.git
workdir /home/financisto

#add '-x test' to exclude tests
run ./gradlew clean build

