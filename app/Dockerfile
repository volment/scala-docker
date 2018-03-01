FROM java:8

ARG version=1.3.10

RUN mkdir -p /usr/local/src/
WORKDIR /usr/local/src/

RUN curl -OL https://downloads.typesafe.com/typesafe-activator/${version}/typesafe-activator-${version}-minimal.zip && \
    unzip typesafe-activator-${version}-minimal.zip && \
    mkdir -p /opt/ && \
    mv activator-${version}-minimal/ /opt/activator && \
    chmod a+x /opt/activator/bin/activator && \
    ln -s /opt/activator/bin/activator /usr/local/bin/activator

WORKDIR /root/

# cache
RUN activator new app minimal-scala && \
    cd app/ && \
    activator run && \
    cd .. && \
    rm -rf app/


WORKDIR /root/app/
CMD ["/bin/bash"]
