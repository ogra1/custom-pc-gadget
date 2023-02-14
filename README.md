# custom-pc-gadget

This is a branch to allow you to build a customized Ubuntu Core gadget snap 
that makes it easy to add the required API key, make changes to the configure hook
of the gadget to apply any gadget-side first-boot configuration or easily add 
any interface slots to the snapcraft.yaml

Building the gadget will re-use the binaries from the existing pc gadget in 
the store so no compilation or additional key signing for secure-boot is happening,
just a re-packing.

## Customizing

To add an API key for the Serial Vault just edit snapcraft.yaml and add a value to the already
existing MODEL_APIKEY variable.

If you need any additional bits for your device onboarding, you can add them
to the prepare-device hook in the snap/hooks/ directory.

To do any custom first-boot configuration you can edit the snap/hooks/configure script.
Do not forget to add the correct interface hooks to the snapcraft.yaml in
case commands added to the hook require them.

You might want to change the `name:` field to not have your package called "custom-pc-gadget".

## Building

simply clone this git tree, install the `snapcraft` snap with 
```
snap install snapcraft --classic
```
and run the `snapcraft`command in the toplevel of the cloned directory.
