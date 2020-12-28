## Usage example

```js
const { ChainLock } = require('@xazab/xazabcore-lib');
const ZMQClient = require('@xazab/xazabd-zmq');
const client = new ZMQClient({
  protocol: 'tcp',
  host: '0.0.0.0',
  port: '29998',
});

(async () => {
    await client.connect();
    client.subscribe(ZMQClient.TOPICS.rawchainlock);
    client.on(ZMQClient.TOPICS.rawchainlock, async (rawChainLockMessage) => {
      const socketChainLock = new ChainLock(rawChainLockMessage);
    });
})();
```
