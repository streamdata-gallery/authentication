---
swagger: "2.0"
x-collection-name: AWS Route 53
x-complete: 0
info:
  title: AWS Route 53 API List V P C Association Authorizations
  version: 1.0.0
  description: 'Gets a list of the VPCs that were created by other accounts and that
    can be associated with a specified hosted zone because you''ve submitted one or
    more CreateVPCAssociationAuthorization requests. Send a GET request to the /2013-04-01/hostedzone/hosted
    zone ID/authorizevpcassociation resource. The response to this request includes
    a VPCs element with a VPC child element for each VPC that can be associated with
    the hosted zone.Amazon Route 53 returns up to 50 VPCs per page. To return fewer
    VPCs per page, include the MaxResults parameter:             /2013-04-01/hostedzone/hosted
    zone ID/authorizevpcassociation?MaxItems=VPCs per page                     If
    the response includes a NextToken element, there are more VPCs to list. To get
    the next page of VPCs, submit another ListVPCAssociationAuthorizations request,
    and include the value of the NextToken element from the response in the NextToken
    request parameter:            /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation?MaxItems=VPCs
    per page&amp;NextToken='
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /2013-04-01/hostedzone/Id/associatevpc:
    post:
      summary: Associate V P C With Hosted Zone
      description: Associates an Amazon VPC with a private hosted zone. ImportantTo
        perform the association, the VPC and the private hosted zone must already
        exist. You can't convert a public hosted zone into a private hosted zone.Send
        a POST request to the /2013-04-01/hostedzone/hosted zone ID/associatevpc resource.
        The request body must include a document with an AssociateVPCWithHostedZoneRequest
        element. The response contains a ChangeInfo data type that you can use to
        track the progress of the request. NoteIf you want to associate a VPC that
        was created by using one AWS account with a private hosted zone that was created
        by using a different account, the AWS account that created the private hosted
        zone must first submit a CreateVPCAssociationAuthorization request. Then the
        account that created the VPC must submit an AssociateVPCWithHostedZone request.
      operationId: associatevpcwithhostedzone
      x-api-path-slug: 20130401hostedzoneidassociatevpc-post
      parameters:
      - in: body
        name: AssociateVPCWithHostedZoneRequest
        description: Root level tag for the AssociateVPCWithHostedZoneRequest parameters
        schema:
          $ref: '#/definitions/holder'
      - in: body
        name: Comment
        description: 'Optional: A comment about the association request'
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the private hosted zone that you want to associate
          an Amazon VPC with
        type: string
      - in: body
        name: VPC
        description: A complex type that contains information about the VPC that you
          want to associate with a private hosted zone
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
  /2013-04-01/hostedzone/Id/authorizevpcassociation:
    post:
      summary: Create V P C Association Authorization
      description: Authorizes the AWS account that created a specified VPC to submit
        an AssociateVPCWithHostedZone request to associate the VPC with a specified
        hosted zone that was created by a different account. To submit a CreateVPCAssociationAuthorization
        request, you must use the account that created the hosted zone. After you
        authorize the association, use the account that created the VPC to submit
        an AssociateVPCWithHostedZone request.NoteIf you want to associate multiple
        VPCs that you created by using one account with a hosted zone that you created
        by using a different account, you must submit one authorization request for
        each VPC.Send a POST request to the /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation
        resource. The request body must include a document with a CreateVPCAssociationAuthorizationRequest
        element. The response contains information about the authorization.
      operationId: createvpcassociationauthorization
      x-api-path-slug: 20130401hostedzoneidauthorizevpcassociation-post
      parameters:
      - in: body
        name: CreateVPCAssociationAuthorizationRequest
        description: Root level tag for the CreateVPCAssociationAuthorizationRequest
          parameters
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: Id
        description: The ID of the private hosted zone that you want to authorize
          associating a VPC with
        type: string
      - in: body
        name: VPC
        description: A complex type that contains the VPC ID and region for the VPC
          that you want to authorize associating with your hosted zone
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - VPC
  /2013-04-01/hostedzone/Id/authorizevpcassociation&amp;maxresults=MaxResults?nexttoken=NextToken:
    get:
      summary: List V P C Association Authorizations
      description: 'Gets a list of the VPCs that were created by other accounts and
        that can be associated with a specified hosted zone because you''ve submitted
        one or more CreateVPCAssociationAuthorization requests. Send a GET request
        to the /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation resource.
        The response to this request includes a VPCs element with a VPC child element
        for each VPC that can be associated with the hosted zone.Amazon Route 53 returns
        up to 50 VPCs per page. To return fewer VPCs per page, include the MaxResults
        parameter:             /2013-04-01/hostedzone/hosted zone ID/authorizevpcassociation?MaxItems=VPCs
        per page                     If the response includes a NextToken element,
        there are more VPCs to list. To get the next page of VPCs, submit another
        ListVPCAssociationAuthorizations request, and include the value of the NextToken
        element from the response in the NextToken request parameter:            /2013-04-01/hostedzone/hosted
        zone ID/authorizevpcassociation?MaxItems=VPCs per page&amp;NextToken='
      operationId: listvpcassociationauthorizations
      x-api-path-slug: 20130401hostedzoneidauthorizevpcassociationampmaxresultsmaxresultsnexttokennexttoken-get
      parameters:
      - in: path
        name: Id
        description: The ID of the hosted zone for which you want a list of VPCs that
          can be associated with the hosted zone
        type: string
      responses:
        200:
          description: OK
      tags:
      - VPC
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---