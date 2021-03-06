Invoking server side code
=========================

Description
===========

The Restlet-GWT API is both a subset and a superset of the Restlet API.

It is a subset because, as mentioned above, parts of the Restlet API
have been deleted, where they depend on Java platform features not
available in the Javascript environment.

It is a superset because the Restlet-GWT API is fully (and only)
asynchronous, which the Restlet 1.1 API is not.  This is necessary to
conform to the behavior of the XmlHttpRequest-based Client, as well as
the strictures of the unthreaded Javascript environment.  In the future,
the Restlet API will expose asynchronous calls, and these will hopefully
converge with the Restlet-GWT API.

Here is a snippet of code (from the downloadable example below) showing
briefly how to instantiate a Client and make an asynchronous GET call:

            closeButton.addClickListener(new ClickListener() {
                public void onClick(Widget sender) {
                    final Client client = new Client(Protocol.HTTP);
                    client.get("http://localhost:8888/ping", new Callback() {
                        @Override
                        public void onEvent(Request request, Response response) {
                            button.setText(response.getEntity().getText());
                        }
                    });
                    dialogBox.hide();
                }
            });

